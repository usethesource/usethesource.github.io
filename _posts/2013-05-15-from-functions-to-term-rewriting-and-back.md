---
layout: post 
published: true
author: Jurgen Vinju
authorlink: http://homepages.cwi.nl/~jurgenv
title: "From functions to term rewriting and back in Rascal"
---

Here's a nifty design element from Rascal that I personally like: functions are actually rewrite rules. The bottom line here is that pattern matching drives dynamic dispatch which results in openly extensible meta programs.

The design choice seems obvious for people who have been programming in ASF+SDF, Stratego and TXL who argue that rewrite rules and strategies were actually just functions.

## Complete functions

In Rascal we write functions in a Java/C/C# like syntax:

```
int fac(int n) {
  if (n == 0)
    return 1;
  else
    return n * f(n - 1);
 }
```

Or slightly shorter and more elegant we could write:

```
int f(int n) = n == 0 ? 1 : n * f(n - 1);
```

In fact, function definitions are just rewrite rules with a funny syntax, the `int n` is actually a pattern that matches integers only and binds them to the variable `n`. This means we can write more concrete patterns and separate the case distinction:

```
int f(0) = 1;
default int f(int n) = n * f(n - 1);
```

The default keyword here indicates to try this alternative only after the other ones, which is obligatory here since Rascal's rules are statically mutually non-overlapping.

## Functions with normal forms

So far we have written a function which is total, i.e. it has to provide a result for all elements of the parameter types. To make this more rewriting-like, where we have normal forms, consider the interaction with constructor functions in the following example:

```
data Bool
  = t()
  | f()
  | and(Bool l, Bool r)
  |   or(Bool l, Bool r)
  ;
  
Bool and(f(), Bool _) = f();
Bool and(t(), Bool b) = b;
```

Here we see the `and` function defined for two cases, where the first argument matches either `t()` or `f()`. It is not defined for any other cases, for example the first argument could be an `or(t(),t())`, so in this sense it is partial. However, the data definition provides a `default` case for the and function, namely to construct the `and` term.

For those of us who are used to rewrite rules, we see rules that are labeled by the sort of the terms that are being rewritten.
Here are some example expressions executed in the console:

```
rascal>and(t(),t())
Bool: t();
rascal>and(f(),t())
Bool: f();
rascal>and(or(t(),t()),t())
Bool: and(or(t(),t()),t())
```

## Modularity by open extensibility

The key benefit of being able to use pattern matching for dynamic dispatch, is extensibility. Suppose we add "maybe" to our logical language in a separate module. This is possible since data signatures are extensible:

```
data Bool = maybe();
```

Now we need to reconsider the semantics of the `and` function, and without changing the original definitions for `and` we simply type these extensions to implement three-valued logic:

```
Bool and(maybe(), maybe()) = maybe()
Bool and(maybe(), true()) = maybe()
Bool and(maybe(), false()) = false()
```

## Pattern matching galore

In Rascal we have a powerful pattern matching operator suite, including:

* list matching (associative), for example: `[*_, elem, _*, elem, _*]`
* set matching (commutative, associative, idempotent), for example: `f({e,*other, f({e,*nested})})`
* deep matching (recursive), as in `/t()` 
* negative matching, as in `!and(_,_)`
* non-linear matching (see above list matching example)
* etc.

These operators may occur in the parameter positions of function definitions, just as they can in switch, visit, {list,set,map} comprehensions, loops, conditionals, etc. As such they give a very broad means to the programmer on how to dispatch between cases. This is only limited by the rule that patterns needs to be mutually exclusive for a certain function.

Here is a function to remove double elements from a list, term rewriting style:

```
list[value] dup([*value a, value e, *value b, e, *value c]) = dup([*a, e, *b, *c])
default list[value] dup(list[value] l) = l;
```

And here is the same function but type parametrized:

```
list[&T] dup([*&T a, &T e, *&T b, e, *&T c]) = dup([*a, e, *b, *c])
default list[&T] dup(list[&T] l) = l
```

## From unlabeled to labeled rules

The big issue with rewrite rules is that they are applied automatically and this is sometimes cumbersome. Functions do not have this issue. Perhaps we should not have defined the boolean semantics so directly, and have wrapped it in a function:

```
data Bool
  = t()
  | f()
  | and(Bool l, Bool r)
  | or(Bool l, Bool r)
  ;
  
Bool eval(and(f(), Bool _)) = f();
Bool eval(and(t(), Bool b)) = b;
```

This reads as labeled rules, we have two rules called "eval" that could be applied but will never be applied automatically unless somebody calls them as a function.

```
rascal>eval(and(f(),t()))
Bool: f()
```

Or, if we wish to apply this rule bottom-up through an entire boolean expression:

```
rascal>visit (and(and(f(),t()),t())) { case Bool b => eval(b); }
Bool: f();
```

In the above we used visit to automate the recursion, but we could have manually implemented the recursion as well:

```
Bool eval(and(t(), Bool b)) = eval(b);
```

## Higher order functions are higher-order rewrite rules

Since our "rules" are actually just functions, we can pass them and combine them just like in any other language that supports higher-order functions. This brings us dangerously close to the expressive power of what term rewriting people call strategies. Anonymous functions (lambdas) can use pattern matching just as any other function by the way.
So we can write expressions such as `(f + g)(x)` where we non-deterministically choose between applying `f` and `g` using pattern matching.


## A note on types

Rascal is a statically typed language, supporting type inference only within the body of functions. We made this choice in order to help keep bodies of functions slim, but without introducing difficult to understand error messages that can be caused by a too smart type inference algorithm. 

This is the reason why all pattern variables in function definitions need to be typed while in normal patterns (nested in the bodies of functions) the types of pattern variables is inferred.

## Conclusion

These were some thoughts on the correspondence between functions and rewrite rules as we put it into Rascal.  We came from a term rewriting world and wanted to keep using their power of pattern matching and open extensibility. Now we are in a world of functional and imperative programming where we can control their application with the flick of a for loop.

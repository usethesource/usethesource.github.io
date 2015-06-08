---
layout: post
published: true
author: Jurgen Vinju
authorlink: "http://homepages.cwi.nl/~jurgenv"
title: From imperative programming to functional programming
---

Rascal features immutable data, but at the same time a number of language constructs which are a lot like "traditional" structured imperative programming: `while`, `if`, etc. Without going into the full power of these constructs in Rascal (featuring lexically scoped backtracking, for example) in this post we go into how _in the same language_ we can program imperatively and functionally at the same time.

The reason Rascal features these two styles is that we want to make it easy for programmers who are used to the imperative paradigm to step into the language. More importantly, we want to make it easy to type classical textbook examples of program analysis and transformations pseudocode rather directly into Rascal syntax. 

### A story about even numbers

Let's write a function that generates all the even numbers in a list up to a certain maximum. We will do it in a few alternative 
ways: from very imperative to very declarative and some steps in between.

```
list[int] even0(int max) {
  list[int] result = [];
  for (int i <- [0..max])
    if (i % 2 == 0)
      result += i;
  return result;
}
```

Now lets remove the temporary type declarations:

```
list[int] even1(int max) {
  result = [];
  for (i <- [0..max])
    if (i % 2 == 0)
      result += i;
  return result;
}
```

To make the code shorter, we can inline the condition in the for loop:

```
list[int] even2(int max) {
  result = [];
  for (i <- [0..max], i % 2 == 0)
    result += i;
  return result;
}
```

In fact, for loops may produce lists as values, using the append statement:

```
list[int] even3(int max) {
  result = for (i <- [0..max], i % 2 == 0)
    append i;
  return result;
}
```

So now, the result temporary is not necessary anymore:

```
list[int] even4(int max) {
  return for (i <- [0..max], i % 2 == 0)
           append i;
}
```

This code is actually very close to a list comprehension already:

```
list[int] even5(int max) {
  return [ i | i <- [0..max], i % 2 == 0];
}
```

And now we can just define even using an expression only:

```
list[int] even6(int max) = [i | i <- [0..max], i % 2 == 0];
```

Or, perhaps we like a set instead of a list:

```
set[int] even7(int max) = {i | i <- [0..max], i % 2 == 0};
```

### What just happened?

In summary:

* We went from 5 lines of code to 1
* We went from 3 control flow constructs (for, if, return) to 0
* We introduced a list comprehension
* All expressions have remained equal
* Intermediate temporary variables dissappeared

What did not happen is any magic. The code still executes the same "algorithm" if you will. The functional programming style in Rascal can be seen as a shorter notation for a more bloated use of imperative control flow constructs.

### The usefulness of imperative control flow constructs

Up front, Rascal's control flow constructs are more powerful than general purpose programming languages control flow constructs. They feature lexically scoped backtracking, lists of conditions, etc.

Even without those advanced features, it is sometimes very handy to split a computation in parts without having to introduce another function abstraction. While exploring a new algorithm, temporary variables can be printed and inspected at debug time, etc.

In Rascal, people often use imperative control flow to _explore_ solutions or _copy_ them from text books, and when they are happy with the algorithm they try and improve the formulation by finding the right functional abstractions. 

### The benefit of functional abstraction over imperative control flow

The real benefits, above brevity and elegance, of the functional style over the imperative style are reusability and extensibility. Smaller functional abstractions are easier to reuse and easier to override. Also, using Rascal's dynamic dispatch using pattern matching (a.k.a. term rewriting) adding new options to algebraic data types can be complemented with adding new cases for functions. In the imperative style such an extension would imply editing existing code, while in the functional style this would not be necessary. See also this other [post](http://www.rascal-mpl.org/from-functions-to-term-rewriting-and-back).


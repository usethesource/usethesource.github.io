---
layout: post 
published: false
author: Jurgen Vinju
authorlink: http://homepages.cwi.nl/~jurgenv
title: "The Language Interaction Design of Concrete Syntax"
---

This post dives into some of the design decisions regarding the manipulation of parse trees and abstract syntax trees in Rascal using _concrete syntax_ notation. 

## Definitions

What we call _concrete syntax_ is a notation for syntax trees that is embedded into the expression notation of meta programming languages. This notation should be equal, or mostly equal, to the surface syntax of the language that is represented by the syntax trees, _and the expressions are still syntactically and statically checked for correctness_. As far as notations for syntax trees go, concrete syntax is a clear winner. Let's compare some expressions representing a piece of C code.

### Concrete syntax

```
if (a && b) { 
  println("a and b"); 
}
```

### Lisp S-expressions

```
(if ((and (id "a") (id "b")) 
    (block 
      ((call (id "println") (args (strconst "a and b")))
    )
)
```

### XML

```
<if>
  <and>
    <id>a</id>
    <id>b</id>
  </and>
  <block>
    <call>
      <id>println</id>
      <args>
        <strconst>a and b</strconst>
      </args>
    </call>
  </block>
</if>
```

### YAML/JSON

```
if:
  - and:
     - id: a
     - id: b
  - block:
     - call:
        - id: println
        - args:
          - strconst: a and b 
```

For the degenerate case of a single node with no children, of course any abstract notation wins. As soon as we have nesting, even marginally interesting code snippets, however, concrete syntax wins by landslide in terms of brevity and cognitive overload.

## Meta Variables

The above examples showed only literal program fragments. One distinguishing feature, however, of concrete syntax is ...

## History

The concrete syntax feature appeared first, as far as I know and please correct me if I am wrong, in the early 1980's in experimental meta programming systems and  algebraic specification systems. There was a concept of _mix fix_ operator syntax where algebraic operators would not only be exclusively prefix, postfix or infix, but all at the same time. This would allow, for example, to define readable algebraic operators with arity larger than two such as `if _ then _ else _`. Some systems started to use BNF to define mix fix functions, and concrete syntax was born. In extreme cases, such as ASF+SDF any context-free grammar rule was allowed to be an operator, while in other systems more restrictions could apply. 

If you are interested in what this all looked like, also in the years after that, the following is a list of names of systems that used or use mixfix operators or concrete syntax in some form or another:

* ASF+SDF
* TXL
* StrategoXT
* Maude
* ELAN
* OBJ
* Smarttools
* Repleo
* SugarJ
* K

People that I know by heart who published on the concrete syntax feature are Annika Aasa, Kent Petersson, Dan Synek, Chris Verhoef, Paul Klint, Eelco Visser, Peter Borovansky, Jan Rekers, Martin Bravenboer, Rob Vermaas, Radu Mereuta, Dorel Lucanu, Jeroen Arnoldus, and yours truly. There must be more.

Concrete syntax should not be confused with string or file templates, such as found in PHP-like template expanders. The difference is that such templates are flat strings that are not statically checked or parsed. With concrete syntax you can not write a pattern that will never match, and you can not write a pattern that will construct a syntactically incorrect output.

Concrete syntax is also strongly related to the older concept of _syntax macros_ (1970's). The similarity is that with syntax macros the user can also define the syntax of functions. The difference is that syntax macros are always expanded into the host language, while with concrete syntax the objects can be manipulated in an arbitrary way, often not to expand into the host language but rather to output a transformed output form.  

So, concrete syntax is not new or novel in any way. It is a good idea nevertheless, and it comes with interesting language usability trade-offs.

## Quotes 

## Types

## Rascal









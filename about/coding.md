---
layout: default
title: Coding Rules
published: true
---

These are guidelines for code style and quality that we follow at UseTheSource.

## General 

* we use [Google's open source style guides](https://github.com/google/styleguide) as the following items are extensions or deviations from this guide.
* maximum line length: 100 
* no tabs for indentation: 4 spaces.
* comments explain any otherwise implicit intent or purpose; otherwise code must speak for itself.

## Java

* all public classes are documented with Javadoc to state their intent and purpose.
* all public methods are documented with Javadoc to state their intent and purpose.
* package names are `io.usethesource.<project>.<sub>`
* use the `@Override` annotation everywhere it's possible.
* clean up all unused imports.

## Rascal

* all public functions have `@synopsis` tags in Rascal tutor format.
* most public functions have `@description` and `@examples` tags in Rascal tutor format.
* tools for languages reside in `lang/<language name>/<sub?>/<tool name>.rsc`
* generic algorithms for analysis reside in `analysis/<algorithm group>/<algorithm>.rsc`
* generic utilities (i.e. for communication) reside in `utils/<utility>.rsc`
* names, unless mapped one-to-one from an external source, follow these rules:
  * references to instances like variables, constructor names, field names, functions, pattern variables, tag names all start with lowercase and continue with camelCaseStyle.
  * names of types, data, syntax, lexical, keyword, layout, and alias types, all start with a capital and continue with CamelCaseStyle.
  * constants are in ALL_CAPS
  * meaningful reserved names, such as `if` for the constructor name are not renamed to avoid the collision but escaped like so: `\if`. This holds for all names.
  * Abstract syntax trees use the typical names as declared in `analysis::m3::AST`: Declaration, Expression, Statement, Type, Modifier.
  * the source location of the original information is always stored in the field `loc src=|unknown:///|`
* the default value for all fields of type `loc` is typically `|unknown://` unless well motivated.
* test functions are located inside the modules of the functionality they test. This is to improve cohesion and lower coupling and to enrich the online documentation with descriptive specifications.
* functions used only for testing purposes are always `private`
* small functions only used by one function are declared inside of the caller's scope as much as possible.
* local helper functions are otherwise made `private`
* `switch` is avoided when pattern based dispatch is also possible, for future extensibility's sake.
* use nullary ADT constructors as "enums", never strings.
* use `loc` source locations as references, qualified names or general identifiers; to avoid strings, captured variables or other fancy usages of first class functions.
* use relations over maps where possible, for future generalizability where suddenly the mapping is not many-to-one anymore. The underlying datastructures for relations gracefully expand.
* Staging before parametrization: introduce an intermediate datatype or relation instead of adding (higher order) parameters to introduce algorithmic variability.
* Positional fields of ADT constructors, when they have a `src` origin field are always ordered by their original position from left you right. The same holds for lists of ADT constructors; they remain ordered by their `src` field, unless the elements do not originate from the same source file anymore.
* Collect and reason about algorithmic answers using relational calculus: union, intersecting, composition, comprehensions, recursion, solve statement; over use the of higher order first class functions and closures. Immutable relations are easier to debug, much easier to extend,  and have fewer bugs in general due to equational reasoning that you loose when using closures over mutable state.
* With respect to error handling:
  * the `Message` ADT is for user expected errors detected in an object language: type checking, linting, etc. which can be reported in an IDE.
  * we collect messages in `list[Message]` sorted by file offset and grouped by source file.
  * functions rather return `void` than return an error code. Instead they throw an exception value when an internal error is detected.
  * exception values are typically a constructor of `RuntimeException` from the `Exception` module. Either use an existing constructor or add your own.
  * Progress is reported through the `util::Monitor` API. This integrates with all programming environments.
  * Interactive UI is built with HTML and JavaScript, using the built-in app server off the REPL on the terminal, the `showInteractiveContent` app server of the IDE or `util::WebServer`. You can use `lang::html` and `lang::json` to streamline this. The Salix library is also recommended. 
    
    

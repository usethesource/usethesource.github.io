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
    
    

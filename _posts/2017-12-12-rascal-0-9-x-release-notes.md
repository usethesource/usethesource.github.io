---
layout: post 
published: true
author: "Jurgen J. Vinju"
authorlink: "http://homepages.cwi.nl/~jurgenv"
title: "Rascal 0.9.x release notes"
---

In this post we report on the Rascal release 0.9.0, which includes all changes since the 0.7.x releases. We have not written release notes for the 0.8.x series (the details are included here). We expect a number of patch releases for 0.9.x, which we report on by updating this post (at its end) when necessary until we move on to 0.10.x. 

The Rascal release 0.9.x includes the following main components:

* Parser and interpreter: parsing and running Rascal programs
* Parser generator: generating parsers for programming languages and domain specific languages
* Eclipse plugin: an IDE for Rascal, partially supported by the new type checker and compiler
* Eclipse plugin generator for DSLs: an IDE generator based on Rascal programs
* Rascal commandline shell: to run Rascal independently from Eclipse
* Standard library: utilities for programming in Rascal, including several (stable) programming language front-ends and general analysis facilities.
* Rascal compiler: the experimental compiler for Rascal
* Rascal type checker: the experimental type checker for Rascal
* TypePal: experimental generic name and type analysis framework
* Salix: a html5-based GUI interaction framework for Rascal
* Shapes: a html5 back-end for the Figure library
* Capsule: the hash-trie set, map and multimap Java library supporting the implementation of Rascal's maps, sets and relations
* Clair: a C++ analysis framework based on the CDT parser
* Split main Rascal Eclipse plugin release from a number of additional libraries, located at a new update site: <https://update.rascal-mpl.org/libs/>
 
The 0.9 release is a landmark release, including a big number of bug fixes and mainly preparations towards releasing a compiled version of Rascal. 

* The most notable new features are:
   1. Rascal type checker
   2. Experimental Rascal compiler
   3. Faster and leaner implementations of maps and relations under-the-hood, based on hash-tries (unfinished)
   4. Fully lazy and streaming string templates
   5. TypePal: a powerful generic type and name analysis framework
   6. Re-implementation of the M3 java Jar extractor
   7. Very fast streamed binary value (de)serialization
   8. Full re-implementation of the tutor documentation generator based on asciidoctor (unfinished)
   9. Typed import/export of JSON data
   10. New "common keyword parameters" support; `data X(int x = 0)` where the field `x` with default `0` is made available to all constructors of the data-type `X` in the current scope.
   11. Calling compiled Rascal functions from Java code using simple Java interface proxy. 
   12. M3 models now use keyword fields instead of annotations
  
* Temporarily disabled features:
   1. syntax highlighting of concrete syntax fragments in the Eclipse Rascal editor is currently turned off
 
* Deprecated features:
   1. annotations as in `anno int X@name;` and their usage `x()@name` is deprecated. Please start using keyword parameters as in: `data X(str name = "")` and `x.name`
   2. asType: `[Type] "string"` in patterns and expressions. Please use the `parse` function for now.


* Other things that were added, improved or fixed:
   1. subscript on lrels added
   2. many, many tests added
   3. refactoring of the REPL api to enable reuse in notebook implementations (see Bacata)
   4. windows compatibility improved
   5. Pattern matchin a bound variable now ignores keyword fields of constructors unless explicitly mentioned
   5. steps towards less dependency on the annotation feature
   6. several bugs around the annotion feature and map indexing fixed
   7. faster field access in the interpreter
   8. compiler is automatically and continuously bootstrapped and validated (no binary code needs committing in the repository)
   9. rationalization and consistency improvement of all the input and output parameters of the compiler and the interpreter via the PathConfig data-type. 
   10. quickcheck random value generator also simplified and made consistent and reusable
   11. clear separation of REPL functionalities and reuse of Eclipse tm.terminal 
   12. clarified and fixed UTF8 encoding details in I/O functions
   13. clarified and fixed URI encoding details in I/O functions
   14. optimized reading from (nested) jar files
   15. much improved efficiency of function calling by the Rascal compiler
   16. additional API for managing external processes
   17. compiler and type-checker support incremental compilation
   18. much faster comparison of source locations
   19. rename of rascal.values (used to be pdb.values) to independent project called "vallang"
   20. support for Java NIO File Channels for (some of the) location schemes.
   21. modular re-implementation of type reification
   22. new modular subsystem to generate classloader instances from URI source locations, e.g. `|system:///|`, `|classpath:///|` and `|file:///path/to/jarFile.jar|` and `|file:///path/to/classFolder|`
   23. interpreter and compiler made maximally code-independent
   24. all projects fully "mavenized"
   25. advanced interactive debugging features of compiled Rascal
   26. REPL and IDE features based on compiled Rascal
   27. integrated compiled Rascal modules as JUnit test runners. 
   28. several fixes in datetime behavior
   29. full implementation of JVM bytecode generation by compiler
   30. parsing ambiguity is now by default an "error" (an exception is raised by the parse function). Using the `allowAmbiguity=true` flag an ambiguous parse forest can still be produced.
   31. added syntax highlighting of parsed source code fragments in the REPL
   32. a `jar+<scheme>:///path/to/jar!/path/in/jar` scheme supports files in jars.
    
### Contributors to the 0.8.x and 0.9.x releases

Thanks! In no particular order the following people have contributed to the 0.9.x releases of Rascal and its supporting libraries or the libraries it supports:

* Paul Klint
* Davy Landman
* Bert Lisser
* Michael Steindorfer
* Mark Hills
* Jurgen Vinju
* Ferry Rietveld
* Tijs van der Storm
* Thomas Degueule
* Lina Maria Ochoa Venegas
* Mauricio Verano
* Rodin Aarssen
* Anya Helene Bagge
* Tim Soethout
* Aiko Yamashita
* Nick Lodewijks
* Jouke Stoel
* Rodrigo Bonifacio
* Yoan-Alexander Grigorov
* Vadim Zaytsev
* Mats Stijlaart
* Magiel Bruntink
* Kevin van der Vlist

Also thanks to all the people who have (clearly) reported bugs and provided smaller pull requests! Your help is much appreciated. 

### Patch releases

* Patch 0.9.1. bootstrap release to introduce new pattern match semantics for `var1 := var2`
* Patch 0.9.2. bootstrap release to fix version number reporting in generated kernels


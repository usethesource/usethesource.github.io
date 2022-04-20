---
layout: post 
published: true
author: "Jurgen J. Vinju"
authorlink: "http://www.rascal-mpl.org"
title: "Rascal 0.23.x release notes"
---

In this post we report on the Rascal release 0.23.x, which includes all changes since the 0.17.x releases. 

---

## Release 0.23.0 - April 10th, 2022

The 0.23.0 release marks the end of the migration of all Rascal supporting libraries (vallang, capsule) and the Rascal interpreter to **Java 11**. The contributors include Paul Klint, Jouke Stoel, Mauricio Verano Merino, Tijs van der Storm, Rodin Aarssen, Arnold Lankamp, Davy Landman, Pieter Olivier and Jurgen Vinju.

We report on intermediate releases 0.18.x, 0.19.x, 0.20.x, 0.21.x and 0.22.x as well, as these had not lead to a release of the Rascal Eclipse plugins or a stable release of the commandline version. 

**Generating Eclipse and VScode Plugins**

This port to Java 11 implies that the current [stable release of the Rascal Eclipse plugin](https://update.rascal-mpl.org/stable/) works again with the latest releases of Eclipse from 2021 and 2022. In the meantime
releases of the [rascal-language-server extension](https://marketplace.visualstudio.com/items?itemName=usethesource.rascalmpl) for VScode have been developed. This has had some impact on the modules in the standard library concerning interaction with DSLs and interactions with the IDE (`util::IDEServices`, `util::Monitor` and `util::IDE`. The old API still works and it is backward compatible in Eclipse. However, if you want to port your DSL to VScode, there are minor changes in how to wrap your extension and new interaction possibilities with the IDE which are not present in Eclipse.

This release works best with Java 11, but not with higher versions. There are still illegal uses of reflective access which need to be resolved before Rascal runs correctly on Java 13 and higher.

**Hosting Releases and Continuous Integration**

* http://releases.usethesource.io is the current place for all Rascal related releases. The Eclipse update site is still at https://update.rascal-mpl.org/stable/
* We migrated our continuous integration scripts to GitHub actions. Thanks to Jenkins for the many years of service and the support from CWI staff and management to keep our servers funded, safe and sound.

**Other changes**

* the `private` access modifier is now idempotent for a name of a function, data-type or syntax non-terminal within single module: in other words, if one of the alternatives is marked private, then all of them are private.
* caching using the @memo tag is done smarter (faster and cleaner cache clearing)
* run-time bugs around type-parametrized ADTs were fixed
* support for constructing the right classpaths by calling `mvn` if pom.xml files are present. This affects the JUnit test runners, the REPL shell, the compiler and type-checker configurations, the setup for terminals in Eclipse projects.
* added functions for inspecting current memory availability and usage
* fixed bugs around prefix matching on concrete trees, simplified its implementation by removing code clones.
* fixed serious bug with prefix shared nullable rules in the parser implementation. 
* fixed race conditions around parser generation for asynchronous usage by the language server protocol
* backtracking over `<==>` and `==>` and `<==` boolean operators is now limited (as limited as backtracking over the `!` boolean operator) 
* case insensitive literals in grammars, such as `'if' Exp 'then' Stat;` are supported better now, also as follow/precede restrictions and keyword reservations (like `Id !>> 'if'`, `Id \ 'if'`) for which an implementation was missing are now supported.
* many regression tests were added as side-effect of the development on the Rascal compiler in the rascal-core project.
* added file watch feature in `IO` module
* added the `lib://libName` scheme for use in `Required-Libraries` in `META-INF/RASCAL.MF` and other places (pathConfig). It resolves to open `project://libName/target/classes` locations or otherwise the jar file that the library is released in and on the classpath.
* added features for recursive copy and recursive move in `IO`
* added lenient option to the JSON parser in `lang::json::IO`
* added utility functions to `util::SystemExec` for easy process creation and termination.
* parse tree filter functions are not called implicitly anymore by the generated parser when building up the tree. Instead a `filter` function is passed to the generated `parse` function where the user can provide filter functions by composing them with `+`. This removes the need for the generated parser function to learn from the current calling scope which functions are available for filtering, and makes the entire parser generator independent of the internals of the interpreter. The new `parser` generator functions work both in the compiled and the interpreted context. Of course, under the hood the implementation reuses the interpreter, until we have bootstrapped the parser generator using the new compiler.
* all Rascal REPLS now support HTML output next to normal string output. Each REPL also serves as a web application host. When a value of type `Content` is the result of evaluation, then the REPL hosts that (Response (Request)) callback until 30 minutes of inactivity. The UI context of the REPL decides how/when and where to show the client side.
* many fixes around higher-order and type-parametrized functions
* moved from the interpreter-specific ICalleableValue to the more abstract IFunction interface to run-time function values.
* rewrote all builtin functions in the standard library to become independent of the interpreter's internals. This is done via constructor arguments of the `@javaClass` implementation classes. These can receive `TypeStore`, `PrintStream` and `IValueFactory` parameters to configure themselves with necessary context of the Rascal runtime.
* `@reflect` is not used anymore by standard library modules. It is deprecated but still supported for now. If you want to make your code robust against compilation by the Rascal compiler, you have to rewrite uses of `@reflect` and receive arguments in your `@javaClass` class constructor.
* All Rascal REPLS print the current release version of the Rascal run-time before anything else.
* Added SourceLocationClassLoader which can construct a JVM classloader instance from references encoded as source location URI. It tries to group file URIs to jar files and forward to URLClassLoader for efficiency's sake. Only ISourceLocationInputResolver schemes which also implement IClassLoaderResolver are supported. We added implementations for all the standard resolvers on the commandline and the necessary ones in the Eclipse context.
* All static errors produced by the new typechecker were fixed in the standard library
* Cleaned up error messages and exceptions in standard library modules (issues largely detected by the typechecker)
* REPLs refactored for use within Bacata (http://github.com/cwi-swat/bacata)


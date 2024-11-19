---
layout: post 
published: true
author: "Jurgen J. Vinju"
authorlink: "http://www.rascal-mpl.org"
title: "Rascal 0.40.x release notes"
---

In this post we report on the Rascal release 0.40.x

<!--truncate-->

## Release 0.40.17 - November 15, 2024

The public release 0.40.x follows release 0.28.x; many improvements have been made in projects that depend on the rascal interpreter and the standard library (the type checker, the VScode extensions, clair, etc.) Some of these improvements depend directly on fixes in the interpreter and additions to the standard library. 

:::info
The Rascal type-checker which is available in the VScode extension is reaching maturity. The `.tpl` file format has changed, which requires everybody to throw the old ones away. The new type checker checks `.tpl` file versions and reports possible conflicts. Use `mvn clean` or remove your `bin` or `target` folders for all your projects and library projects today.
:::

:::warning
Eclipse support for Rascal will shortly be archived. After more than three years of deprecation, no more maintenance releases on the IDE plugins will be released. Also we will be archiving the git repositories of the following projects:
* rascal-eclipse
* impulse
* rascal-eclipse-libraries

Note that the Java support which is based on Eclipse JDT will remain to be supported. See also below for the new features.

Porting the Rascal LSP servers to the Eclipse LSP client would be interesting. If you are interested in contributing, we are all ears.
:::

The support for XML, JSON and HTML as exchange formats has been improved or completely rewritten. The main feature that was added was the optional `loc src` keyword field that provides the exact location of each node as it appears in the XML, HTML or JSON source text.

A new `mvn://` scheme was added to be able to address with brief but unique notation the jar files in the local M2 repository. It supports two modes:
* `mvn://groupId!artifactId!optionAlComplexVersionString/pathInsideJar`, shorthand for identifying artifacts inside the mvn repository on this machine.
* `mvn:///path/inside/m2/repository/jarFile.jar` for exploring the mvn repository from its root.
If `maven.repo.local` is set, then that is the root of the M2 repository. Otherwise if `~/m2/.repository` exists (in the users ome directory) then that is used. Otherwise `mvn` is executed with `-Dexpression=settings.localRepository` to extract the setting from the current `pom.xml` file. This is _not_ the official order as `mvn` resolves these configuration options; but it was chosen for the sake of efficiency.

A great deal of tests were fixed, enhanced or extended as a side-effect of the compiler project. Another visible aspect of the progress of the compiler is that now all Rascal runtime values (from vallang and beyond) now support `getFingerprint()` methods which help in optimizing pattern matching and dispatch in generated code by the compiler. These  methods' return values have become a strict contract for future implementations of Rascal values, including parse trees and reified types and first-class functions.

### The following issues were solved 

* String `visit` with unicode characters had a bug
* `util::ShellExec` had some IO synchronization issues which were resolved.
* The JUnit test runners report exceptions better now.
* The broken and unused `stdout://` and `stdin://` resolvers were removed.
* The `IO::watch` functionality was improved for logical source locations. It is now fully functional on all systems with a JVM. However the system is still too slow on Mac to work effectively in an interactive development environment.
* [Identical inner functions are flagged as code clones](https://github.com/usethesource/rascal/issues/2067)
* [Unsupported splice pattern causes NULL pointer exception inside interpreter](https://github.com/usethesource/rascal/issues/2071)
* [Add-assign of incompatible set types does not raise error](https://github.com/usethesource/rascal/issues/2056)
* [Missing a "info" or "warning" message at the call-site of @deprecated functions](https://github.com/usethesource/rascal/issues/2055)
* [deprecated module has squiqqlies over the entire file](https://github.com/usethesource/rascal/issues/2052)
* [`rascalTModelForLocs` does not return TModel](https://github.com/usethesource/rascal/issues/2050)
* [(common) keyword field projecten out of ADT produces dynamic instead of static type for the static type result.](https://github.com/usethesource/rascal/issues/2049)
* [Internal crash instead of static error for relation field projection on unlabeled relation types](https://github.com/usethesource/rascal/issues/2048)
* [Typechecker fails to report error on invalid function return type](https://github.com/usethesource/rascal/issues/2046)
* [Type checker reports undefined module after edit](https://github.com/usethesource/rascal/issues/2044)
* [Rascal check crashed unexpectedly with: MultipleKey at: |std:///Map.rsc|(2659,708,<109,0>,<130,54>)](https://github.com/usethesource/rascal/issues/2039)
* [Progress monitor's utf-8 check only works in interactive terminals](https://github.com/usethesource/rascal/issues/2032)
* [Unexpected 'Ambiguous pattern type' error](https://github.com/usethesource/rascal/issues/2030)
* [In overlapping names, order matters for the typechecker](https://github.com/usethesource/rascal/issues/2026)
* [`Maybe::nothing` causes wrong type if used in adt keyword parameters](https://github.com/usethesource/rascal/issues/2025)
* [Two binds on both sides of the OR operator don't work if they are in a nested expression.](https://github.com/usethesource/rascal/issues/2024)
* [Rascal-core is generating prints in the monitor](https://github.com/usethesource/rascal/issues/2023)
* [Rascal type-checker crashed unexpectedly with: No module scope found for ...](https://github.com/usethesource/rascal/issues/2021)
* [What to expect: common keyword parameter of data declaration and keyword parameter of constructor have the same name](https://github.com/usethesource/rascal/issues/2019)
* [add function to identify possible addition of cycles on nodes](https://github.com/usethesource/rascal/issues/2018)
* [Typechecker reports used variable as unused](https://github.com/usethesource/rascal/issues/2014)
* [Overloads with different type parameter names cause error](https://github.com/usethesource/rascal/issues/2013)
* [Function that only throws exception is expected to have `bool` return type](https://github.com/usethesource/rascal/issues/2012)
* [Typechecker disallows assigning `nothing()` to field of type `Maybe`](https://github.com/usethesource/rascal/issues/2007)
* [Typechecker fails on `analysis::typepal::TypePal`](https://github.com/usethesource/rascal/issues/2006)
* [string editor `visit` fails with unicode matches.](https://github.com/usethesource/rascal/issues/2005)
* [Type constructor subtype issue?](https://github.com/usethesource/rascal/issues/2003)
* [Type checker infers `value` for known-type tuple wildcards in iterator](https://github.com/usethesource/rascal/issues/1996)
* [Type of generator leaks](https://github.com/usethesource/rascal/issues/1995)
* [`type` constructor doesn't accept keyword parameters starting with `\` symbol](https://github.com/usethesource/rascal/issues/1991)

On the Rascal run-time engine (vallang) these issues were resolved:

* [Add \f escape in string constants back into vallang StandardTextReader](https://github.com/usethesource/vallang/issues/270)
* [StandardTextReader does not support `\f` escape while rascal does](https://github.com/usethesource/vallang/issues/268)
* [Drop xz-java dependency](https://github.com/usethesource/vallang/issues/252)
* [Entry Buckets in ShareableValuesHashSet typically nest 4 or 5 times during a transitive closure on source locations (call graph)](https://github.com/usethesource/vallang/issues/235)
* [TypeFactory use of `checkNull` shows up on profiles](https://github.com/usethesource/vallang/issues/233)
* [Performance regression for transitive closure on large `rel[loc,loc]`](https://github.com/usethesource/vallang/issues/230)
* [Add identity ("kind") to types (for the benefit of generated code and runtime system)](https://github.com/usethesource/vallang/issues/209)
* [Add informative error messages to asserts](https://github.com/usethesource/vallang/issues/158)
* [evaluate efficiency of new hash-consing design in pr #131](https://github.com/usethesource/vallang/issues/135)
* [add IString::asReader to stream _from_ strings](https://github.com/usethesource/vallang/issues/71)


### Standard library maintenance

* Accurate and correct parsers of Windows and Unix file paths were added to the standard library. This includes a new `unc://` resolver to accurately represent the semantics of UNC paths, and `cwdrive://` which can represent the current working directory on a given drive letter on Windows.
* `HTMLElement(loc src = |unknown:///|)` was added to position every tag from start to end via the `src` attribute.
* The documentation strings were ported from `@doc{ }` notation to `@synopsis{..}, @description{..}, @examples{..}, @benefits{..}, @pitfalls{..}` separate tags. 
* The `@deprecated{..}` tag is now also used during API documentation generation. It is rendered between the synsopsis and the declaration signature.
* The Box language for automatic string formatting was revived and its box2text algorithm was optimized. See `lang::box`
   * Box2text was re-implemented using list comprehensions and list splicing for efficiency and brevity.
   * Box arrays (tables) were fixed and finalized, and utility support for mapping lists to tables was added.
   * Box "groups" were added (ported from ASF+SDF) as a means to easily generate boxes from (separated) lists.
   * The concepts of fonts and highlighting were completely removed from Box, as this is an orthogonal feature
implemented elsewhere by highlighter algoriths and mappings to HTML. The new trick is to use Box to format a file,
then reparse that file and map it to ANSI or HTML or other markup formalisms.
   * the NULL box was added as a convenience for plugging holes and not loose parity or other counts.
   * Tests for Box2text were added.
   * Tree2Box is a new language-parametric  formatter that maps any parse tree to Box using default heuristics. They trigger on the shape of production rules as they are typically found in programming languages. Tree2Box is a re-implementation of the
`pandora` tool of the ASF+SDF Meta-Environment, but written in Rascal instead of C+ApiGen. You can override default behavior by adding rules for your exceptional language constructs.
* The CSV model now has origin fields for Tables, Records and Fields: `loc src=|unknown:///`, such that CSV files can be 
parsed and treated as (DSL) source code.
* `lang::json::IO` now has full origin tracking support.
* `util::Monitor` progress monitoring is now also supported on textual interfaces using UTF8 and ANSI support for pretty bars. If UTF8 is not supported by the terminal, it used ASCII art. If ANSI is not available, it defaults to normal event logging prins on the console. The progress bar will always default to the latter if in a CI environment of if `-Drascal.monitor.batch` is set.
* The progress monitors for module importation in the interpreter and parser generator were rationalized.
* In `lang::rascal::grammar::storage::ModuleParserStorage` a new feature for saving generated parsers to disk and loading them again was added. It follows the interface design of `ParseTree::parsers`. You can load a saved parser and used it as if 
just generated with `parsers`.
* `lang::rascal::vis::ImportGraph` was added as a port of the ASF+SDF Meta-Environment import graph visual.
* `lang::std::ANSI` is an almost complete specification of the ANSI standard for character markup.
* `util::Clipboard` was added to give programmatic access to the systems copy/paste feature for textual content. The feature starts up lazily so the first call to `copy` or `paste` is slower than subsequent calls. In a headless environment `copy` always returns the empty string and `paste` simply has no effect. Paste and copy are "thread friendly" in that they will produce or reproduce a string that at one time was in the system's copy/paste buffer. However, it is not necessarily the last entry and other processes may overwrite the buffer while the Rascal programming is running that has just written to it.
* `util::Eval` was refactored and reimplemented for efficiency and robustness, following the TutorCommandExecutor design from the rascal-tutor project. Eval instances are now fully configured via `PathConfig`.
* The concept of CodeActions was added to `util::IDEServices`, they also extend error `Message` constructors. CodeActions can be used to register quickfixes and other code related actions to editor positions. The positions are either directed by the error message they are attached to, or via syntax-directed pattern matching. This feature plays well with the LanguageServer features in rascal-lsp.
* added `util::Reflective::newRascalProject` to set up an empty project template with the right RASCAL.MF file and pom.xml file.
* `ManifestRunner.java` was removed because it was unused.
* The `benchmark:///` resolver was removed, so was `test-temp:///`, `test-data:///` and `test-modules:///`.
* The `memory://` resolver now supports independently garbage collectible filesystems per authority name.

### Java support

The Java model has received big maintenance love and attention, including improvements to the generic M3 model:
* Bumped and upgraded  to the JDT version from Eclipse 2020-03, then upgraded mapping support up to and including JLS-14.
* Up to JLS14 all new Java constructs were added to the AST and the M3 Core model. The previous standard we supported was JLS8.
* The AST nodes in `lang::java::m3::AST` now all satisfy the AST contract in `analysis::m3::AST`. This means that
all source code elements are represented in the tree, annotated with `src` origins and ordered from left-to-right as
they were in the original source file.
* The constructors: `enum`, `enumConstant`, `compilationUnit`, `class`, `interface`, `method`, `field`, etc., all received
extra positional parameters for the concept of modifiers. Before these were modelled as keyword parameters, but 
that invalidated the earlier mentioned AST contract.
* An AST and M3 model of the Java 9 module system was added.
* The `isSuper` boolean was removed from the AST definition of `methodInvocation`n and `new` calls, also to satisfy the AST contract.
* Java Annotations AST constructors were moved from `Expression` to `Modifier`.
* String based unary and binary operator constructors for Expressions were unfolded to a constructor for each operator, i.e. `plus(Expression, Expression)` instead of `binop(Expression, "+", Expression)`
* `lang::java::m3::AST` was documented and so was `analysis::m3::AST`
* `lang::java::m3::Core` was documented and so was `analysis::m3::Core`
* `composeM3` was generalized for any number of keyword fields which are either sets or lists. This makes it language-independent from now on.
* `m3SpecificationTest` checks for the internal sanity and completeness of an M3 model. Can be used to test language front-ends.
* `Java2ObjectFlow` was upgraded for all the changes in the AST constructors. However it may still need extension for new constrtructors like lambda expressions.
* Lambda's were added to `Expression`
* Method references were added to `Expression`
* Intersection types were added to the Type AST class
* The bounds constructors of Type ASTs were renamed from `upperbound` and `lowerbound` to `super` and `extends`.
* Java versions are now specified as constructors of the `Language` data type, for accurate description of the JLS language level the user needs to reflect.
* M3 extraction from JVM binary class files was maintained and now also supports language features up to JLS14.  In particular the Java 9 module system was added to the mapping.
* Tracebility with origin tracking was improved for both source code and binary classfile analysis, so if NPE's happen a clear cause can be printed.


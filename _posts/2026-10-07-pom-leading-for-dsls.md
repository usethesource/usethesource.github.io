---
layout: post 
published: true
author: "Toine Hartman"
authorlink: "http://www.rascal-mpl.org"
title: "POM-leading for DSL projects"
---

In this post we report on the important changes to dependency resolution in Rascal 0.43.0 and Rascal LSP 2.23.0.

<!--truncate-->

## POM-leading for DSL projects - October 10, 2026

Since some time, Rascal projects have been gradually moving away from the manifest-based project configuration towards Maven's [POM](https://maven.apache.org/pom.html). Library depencies need to be specified in the POM. These libraries are resolved (and, if needed, downloaded) in the local Maven repository and used by Rascal tools like the VS Code extension (IDE features) and the Maven plugin (`mvn compile`).

However, the `rascal` and `rascal-lsp` dependencies were treated differently. In many cases, it was not even necessary to explicitly specifiy them in the POM, because they were implicitly added. And even if specified, their version would often be ignored in the IDE, due to implementation constraints.

Not anymore! In the past year, we have reworked many parts of Rascal and the VS Code extension. This allows the extension to follow the POM more closely, leading to predictable and transparent dependency versions in Rascal projects. REPLs in VS Code and type-checks in the IDE will now use the Rascal standard library version from the POM, and language servers registered using `registerLanguage` will run with the specified Rascal and LSP versions.

In order to work with the newest release of the VS Code extension, new and existing projects should be set up with the proper dependencies. Rascal language projects might require code changes as well.

### Modifying existing Rascal projects

Any new or existing project requires an explicit dependency on Rascal `0.43.0` in the POM:

```xml
<dependencies>
    <dependency>
        <groupId>org.rascalmpl</groupId>
        <artifactId>rascal</artifactId>
        <version>0.43.0</version>
    </dependency>
    <!-- other dependencies -->
</dependencies>
```

### Modifying existing language projects

Language projects are projects that use the [`util::LanguageServer` library](https://www.rascal-mpl.org/docs/Packages/org.rascalmpl.rascal-lsp/Library/util/LanguageServer/) and/or use [`registerLanguage`](https://www.rascal-mpl.org/docs/Packages/org.rascalmpl.rascal-lsp/Library/util/LanguageServer/#util-LanguageServer-registerLanguage) in the REPL. These projects require additional changes. First of all, they need a POM dependency on the newly released version of Rascal LSP, since this dependency is not implicitly derived from the development environment anymore.

```xml
<dependencies>
    <dependency>
        <groupId>org.rascalmpl</groupId>
        <artifactId>rascal-lsp</artifactId>
        <version>2.23.0</version>
    </dependency>
    <!-- other dependencies -->
</dependencies>
```

In any call to `registerLanguage`, the parameter should now contain a complete path config. This path config can be obtained by [`util::Reflective::getProjectPathConfig`](https://www.rascal-mpl.org/docs/Library/util/Reflective/#util-Reflective-getProjectPathConfig) with the `interpreter_external` mode. This mode ensures that the the path config will be strictly based on the POM.

```rascal
import util::LanguageServer;
import util::Reflective;

void main() {
    PathConfig pcfg = getProjectPathConfig(|project://my-project|, mode=interpreter_external());
    registerLanguage(language(
        pcfg,
        "MyLanguage",
        {"mylangext"},
        "language::main::module",
        "contibutionsFunction"
    ));
}
```

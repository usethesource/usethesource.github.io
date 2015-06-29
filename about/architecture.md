---
layout: default
title: Architecture
published: true
---

These are common design decisions for UseTheSource software in different stages of development.
The decisions and the fact that they are shared among the projects is motivated by striving for continuity, integration and adoption.

## Programming Languages, Frameworks and Platform 

* We try to avoid external dependencies, and use the JVM as much as possible;
* External dependencies we resolve using the maven grand central (no embedded jars) or standard Eclipse update sites;
* Eclipse Luna for IDE features and UI integration.

## Continuous Integration and Testing

* We run all projects on the UseTheSource Jenkins instance;
* Builds are triggered automatically after a push to github.

## Version Management

* All projects use git;
* All projects are hosted on github in the usethesource organization;
* All features are developed on a branch different from `master`;
* A new `master` is pushed only if the unit tests have been run successfully;
* Github issue id's are used in commit messages `fixes #23`.

## Issue Trackers

The issue tracking system is used as task list and issue management system at the same time.

* We use the github issue tracker;
* Issues are first registered with github and then resolved;
* New Features are also registered as issues.

## Release and Deployment 

* All projects are continuously released on the `unstable` update site and maven repository (add link);
* Projects have an independent release and deployment cycle when possible; but if dependencies are broken then release and deployment is synchronised;
* External dependencies which are not on the Eclipse standard update sites and not in the Maven Grand Central get a separate feature released indepedently on our update site.

## Websites

* We use github pages and a common infrastructure (add link) for each project's website.

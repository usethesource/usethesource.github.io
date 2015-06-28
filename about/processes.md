---
layout: default
title: Community Processes
published: true
---

These are recipes for how things are organized in the UseTheSource community.

## Organization

UseTheSource is organized as a flat hierarchy with of roles with Board Members on top, Project Owners in the middle and Contributors below. The Board Members take responsibility for the integration and presentation of the entire community. The Project Owners have the responsibility for a specific project (one project may have several owners), and the Contributors are responsible for each contribution made. Users are people who download and apply the projects and possible submit pull requests or issues. Specific rights and responsibilities for each role are mentioned below.

The current board members are Paul Klint, Jurgen Vinju and Tijs van der Storm.

## Project Incubation Process

1. Contributors propose the start of a new project to The Board Members at UseTheSource by:
   * creating an issue at <https://github.com/usethesource/usethesource.github.io/issues>; 
   * naming the new project; 
   * linking the github repository; 
   * proposing a Project Owner;
   * including a short motivation which details intended audience, distinguishing features, possibly dependence on and usefulness for other UseTheSource projects, and references to technical reports and/or academic papers.
2. Board Members evaluate the proposal by the following merits:
   * On-topic for UseTheSource; 
   * Relevant and interesting for a specified audience;
   * Viability for a 5 year horizon;
   * Well tested (e.g. including automated unit and integration tests and verifiable usage by early adopters);
   * Adherence to the UseTheSource architecture and coding rules;
   * Adherence to the UseTheSource open-source licenses;
   * Signed [UseTheSource Contributor Agreements](agreement.html) by all authors of the code;
3. Discussion is logged at <https://github.com/usethesource/usethesource.github.io/issues>, leading up to a unanimous "go" or "no-go" decision by the Board Members.
4. When a "go" decision is made:
   * The project is transferred to the usethesource organization on github;
   * A new webpage is instantiated;
   * The project is added to [the projects page](../projects/);
   * The project is included in the continuous integration environment;
   * The issue is closed at <https://github.com/usethesource/usethesource.github.io/issues>.
5. When a "no go" decision is made:
   * The issue is closed at <https://github.com/usethesource/usethesource.github.io/issues>
   * Contributors can propose again in the future by re-opening the issue at <https://github.com/usethesource/usethesource.github.io/issues>

## Contributor Project Membership Process

## Project Development Process

## Project Release Process

## Project User Support Process

* Github issues is used for user feedback, questions, feature requests and bug reports;
* Any pull request by a User over 2 lines of code requires a signed [UseTheSource Contributor Agreement](agreement.html) by the author;
* The stackoverflow.com site is promoted among Users for questions regarding usgin any of UseTheSource projects (tag with the given language name/library/tool).

## Architectural Change Process

1. Design decisions which influence all or many of the UseTheSource projects are registered as an issue at <https://github.com/usethesource/usethesource.github.io/issues> by Project Owners or Contributors;
2. Project Owners discuss the change for acceptance and finetune the planning regarding the implementation of the change;
3. The ultimate decision for implementing the change lies with the Board Members, who have to agree unanimously and sollicit support from the Project Owners of all affected projects;
4. A unique and new branch name is decided upon;
5. New issues are registered with the respective projects for implementing the change;
6. All relevant projects are branched using the given branch name;
7. When all projects are stable on said branch, the branches are merged to master and the issue is closed.

## Project Burial Process

1. Project Owners or Board Members propose the end-of-life of a UseTheSource project at <https://github.com/usethesource/usethesource.github.io/issues>.
   * This event is expected to be extremely rare, and mirrors the Incubation Process.
2. Board Members and evaluate the proposal by the following merits:
   * No other UseTheSource projects depend on the given project;
   * Viability is arguably in danger;
   * Discontinuation of the project is beneficial to the Project Owners, Contributors;
   * Discontinuation of the project is not harmful for known Users.
3. Discussion is logged at <https://github.com/usethesource/usethesource.github.io/issues>, leading up to a unanimous "go" or "no-go" decision by the Board Members.
4. When a "go" decision is made:
   * The github repository is moved from usethesource to a different organization or user on github (e.g. the Project Owner);
   * The project is removed from the continuous integration setup;
   * The project's website is redirected to the github repository page;
   * The project is listed at the [projects page](../projects/) for historical reference (with a link to the new location);
   * the issue is closed at <https://github.com/usethesource/usethesource.github.io/issues>;
5. When a "no go" decision is made:
   * The issue is closed at <https://github.com/usethesource/usethesource.github.io/issues>
   * Project Owners or Board Members can propose again in the future by re-opening the issue at <https://github.com/usethesource/usethesource.github.io/issues>

---
layout: default
title: Community Processes
published: true
---

These are recipes for how things are organized in the UseTheSource community.

## Organization

UseTheSource is organized as a flat hierarchy with of roles with Board Members on top, Project Owners in the middle and Contributors below. The Board Members take responsibility for the integration and presentation of the entire community. The project owners have the responsibility for a specific project (one project may have several owners), and the contributors are responsible for each contribution made. Specific rights and responsibilities for each role are mentioned below.

The current board members are Paul Klint, Jurgen Vinju and Tijs van der Storm.

## Incubation Process

1. Contributors propose the start of a new project to The Board Members at UseTheSource by:
   * creating an issue at <https://github.com/usethesource/usethesource.github.io/issues>; 
   * naming the new project; 
   * linking the github repository; 
   * proposing a Project Owner;
   * including a short motivation which details intended audience, distinguishing features, possibly dependence on and usefulness for other UseTheSource projects, and references to technical reports and/or academic papers.
2. Board Members evaluate the proposal by the following merits:
   * on-topic for UseTheSource; 
   * relevant and interesting for a specified audience;
   * viability for a 5 year horizon;
   * well tested (e.g. including automated unit and integration tests and verifiable usage by early adopters);
   * adherence to the UseTheSource architecture and coding rules;
   * adherence to the UseTheSource open-source licenses;
   * signed [UseTheSource Contributor Agreements](agreement.html) by all authors of the code;
3. Discussion is logged at <https://github.com/usethesource/usethesource.github.io/issues>, leading up to a unanimous "go" or "no-go" decision by the Board Members.
4. When a "go" decision is made:
   * the project is transferred to the usethesource organization on github;
   * a new webpage is instantiated;
   * the project is added to [the projects page](../projects/);
   * the project is included in the continuous integration environment;
   * the issue is closed at <https://github.com/usethesource/usethesource.github.io/issues>.
5. When a "no go" decision is made:
   * the issue is closed at <https://github.com/usethesource/usethesource.github.io/issues>
   * contributors can propose again in the future by re-opening the issue at <https://github.com/usethesource/usethesource.github.io/issues>

## Development Process

## Release Process

## User Support Process

* github issues for user feedback, questions, feature requests and bug reports
* stackoverflow.com for questions regarding programming in our languages (tag with the language name)

## Architectural Change Process

1. Design decisions which influence all or many of the UseTheSource projects are registered as an issue at <https://github.com/usethesource/usethesource.github.io/issues> by Project Owners or Contributors;
2. Project Owners discuss the change for acceptance and finetune the planning regarding the implementation of the change;
3. The ultimate decision for implementing the change lies with the Board Members, who have to agree unanimously and sollicit support from the Project Owners of all affected projects;
4. A unique and new branch name is decided upon;
5. New issues are registered with the respective projects for implementing the change;
6. All relevant projects are branched using the given branch name;
7. When all projects are stable on said branch, the branches are merged to master and the issue is closed.

---
title: AI rules
keywords:
  - AI
  - LLM
  - license
  - copyright
---

The application of AI -in particular Large Language Models (LLMs)- is interesting for 
UseTheSource projects. Although most of the practical consequences are already outlined [elsewhere](/about/index),
we explain some of the consequences here for our contributors. Two different aspects:

1. AI applied to UseTheSource source code itself: **no**.
2. Experimental AI applications of {sofware,natural} language processing: **yes, with caution**.

#### AI applied to UseTheSource source code itself: no

When AI is used to _generate_ or _transform_ source code of UseTheSource projects be **aware**
that you might easily be failing compliance with the [Contributor License Agreement](https://github.com/usethesource/usethesource.github.io/blob/master/about/index.md#:~:text=Contributor%20License%20Agreement) that you signed:

> * [x] Each contribution which I submit is and will be an original work of authorship and I can legally contribute it to open-source.
> * [x] To the best of my knowledge each contribution I submit will not violate any copyright laws, trademarks, patents, or other intellectual property rights.

Conclusion: you currently can't use an LLM to literally generate or transform code or (inline) documenation for our projects. 

#### Experimental AI applications of {software,natural} language processing: yes, with caution.

All kinds of applications of LLM's in UseTheSource projects have common issues. A UseTheSource contributor applying an LLM in their project must:
1. If code **generation** or **transformation** is the topic, see [above](#ai-applied-to-usethesource-source-code-itself-no) for issues with licensing and other rights. 
1. If **publication** of AI generated language is a feature (arxiv, conference, issue tracker, online discussion), then see [above](#ai-applied-to-usethesource-source-code-itself-no), with code replaces by natural language text.
1. Manage and communicate **LLM licenses** to users (and their users). 
2. Manage and communicate the **environmental impact** of the training and usage of LLMs. 
3. Manage and communicate the effect on the level of **expertise** in the target community. 
4. Give the **user agency** over the choice of LLM to use for each task, during download/install, or during webservice login.


---
title: AI rules
---

The application of AI -in particular Large Language Models (LLMs)- is interesting for 
UseTheSource projects. Although most of the practical consequences are already outlined [elsewhere](/about/index),
we explain some of the consequences here for our contributors. Two different aspects:

1. AI applied to UseTheSource source code itself
2. AI applications of {sofware,natural} language processing

#### AI applied to UseTheSource source code itself

When AI is used to _generate_ or _transform_ source code of UseTheSource projects be **aware**
that you might easily be failing compliance with the [Contributor License Agreement](https://github.com/usethesource/usethesource.github.io/blob/master/about/index.md#:~:text=Contributor%20License%20Agreement) that you signed:

> * [x] Each contribution which I submit is and will be an original work of authorship and I can legally contribute it to open-source.
> * [x] To the best of my knowledge each contribution I submit will not violate any copyright laws, trademarks, patents, or other intellectual property rights.

"To the best of my knowledge" in this case means that you know that you don't know if the AI you used is violating any rights.
Conclusion: you currently **can not use an LLM** to literally generate or transform code for our projects.

The consequences of failing this rule could be disastrous for UseTheSource and Rascal. 
So please do keep in line. Your code, your responsibility.

#### AI applications of {software,natural} language processing

As LLM's are (natural) language processors and UseTheSource is all about software language processing, there is opportunity to combine the two. All kinds of experiments regarding the use of LLM's in UseTheSource projects have common issues. At least you as a UseTheSource contributor must:
1. Manage and communicate usage **licenses** of existing LLMs (open-source or not), and make sure your users are also made aware of their rights and obligations. Especially privacy is an interesting topic to manage, but also code ownership, licenses and other rights
2. Manage and communicate the **environmental impact** of the training and usage of LLMs. And also communicte clearly to users what this impact was/is.
3. Understand and manage the level of **expertise** in the target community for their project. Is the LLM helping with complex tasks or is it hiding essential complexity?
4. Give the **user agency** over the choice of LLM to use for each task (download and install, or webservice connectivity). Possibly also the users of our users.
   * this means never linking and LLM into a jar, or downloading it just-in-time under-the-hood.
   * this also means users have to provide their own credentials to AI behind web services



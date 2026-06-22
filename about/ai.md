---
title: AI rules
---

The application of AI -in particular Large Language Models (LLMs)- is interesting for 
UseTheSource projects. Although most of the practical consequences are already outlined [elsewhere](/about/index),
we explain some of the consequences here for our contributors.

#### AI applied to UseTheSource source code 

When AI is used to _generate_ or _transform_ source code of UseTheSource projects be **aware**
that you might easily be failing compliance with the [Contributor License Agreement](https://github.com/usethesource/usethesource.github.io/blob/master/about/index.md#:~:text=Contributor%20License%20Agreement) that you signed:

> * [x] Each contribution which I submit is and will be an original work of authorship and I can legally contribute it to open-source.
> * [x] To the best of my knowledge each contribution I submit will not violate any copyright laws, trademarks, patents, or other intellectual property rights.

"To the best of my knowledge" is this case means that you know that you don't know if the AI you used is violating any rights.

Conclusion: you currently **can not use an LLM** to generate or transform code for our projects!

To work around this, you could explore the design space AI, and then 
write your production ready code **from scratch**. You can learn knowledge and skills from the AI, but not literal code.

The consequences of failing this advise could be huge for UseTheSource and Rascal (disastrous), 
so please do keep in line. Your code, your responsibility.

#### AI applications for the UseTheSource domain

As LLM's are (natural) language processors and UseTheSource is all about software language processing, there is ample opportunity to combine the two and create a flywheel effect. All kinds of experiments regarding the use of LLM's to replace or complement the language processors we have are welcome.

Be aware of the usage licenses of existing LLMs (open-source or not), and make sure your users are also made aware of their rights and obligations. Especially privacy is an interesting topic to think about.

Advice:
* never directly link an LLM into a UseTheSource project. Always let the users download or call them.
* never release pre-trained LLM's with a UseTheSource jar.
* always give the user agency over the choice of LLM to use for each task (download and install, or webservice connectivity)


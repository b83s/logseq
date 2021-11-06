---
title: GTP-3
---

- [GPT-3: The New Mighty Language Model from OpenAI](https://towardsdatascience.com/gpt-3-the-new-mighty-language-model-from-openai-a74ff35346fc)
	 - GPT-3: The New Mighty Language Model from OpenAI

	 - Introduction

	 - [OpenAI](https://openai.com/) recently [released](https://arxiv.org/abs/2005.14165) pre-print of its new mighty __language model__ GPT-3. Its a much bigger and better version of its predecessor GPT-2. In fact, with close to 175B trainable parameters, GPT-3 is much bigger in terms of size in comparison to anything else out there. Here is a comparison of number of parameters of recent popular pre trained NLP models, GPT-3 clearly stands out.

	 - ![Image for post](https://miro.medium.com/max/60/1*C-KNWQC_wXh-Q2wc6VPK1g.png?q=20)

	 - ![Image for post](https://miro.medium.com/max/582/1*C-KNWQC_wXh-Q2wc6VPK1g.png)

	 - <

	 - Terminologies

	 - Before we deep dive, it may be useful to define some commonly used terminologies:

	 - **NPL Tasks:** These are tasks which have something to do with human languages, example — Language Translation, Text Classification (e.g. Sentiment extraction), Reading Comprehension, Named Entity Recognition (e.g. recognizing person, location, company names in text) 

	 - **Language Model**s: These are models which can predict the most likely next words (and their probabilities) given a set of words (think something like Google query auto-complete). Turns out these type of models are useful for a host of other tasks although they may be trained on mundane next word prediction 

	 - **Zero / One / Few shot learning:** Refers to model’s ability to learn a new task by seeing zero / one / few examples for that task 

	 - **Transfer Learning:** Refers to the notion in Deep Learning where you train a model for one task (example object detection in images) , but the ability to leverage and build upon that for some other different task (example assessing MRI scans). After massive success in Computer Vision, its in vogue in NLP these days. 

	 - **Transformer Models**: Deep learning family of models, used primarily in NLP, which forms the basic building block of most of the state-of-the-art NLP architectures these days. You can read more about __Transformers__ at one of my earlier [blog](/recent-advancements-in-nlp-2-2-df2ee75e189) 

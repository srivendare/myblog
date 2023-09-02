---
title: How to form an effective prompt to ChatGPT
author: "Rui"
categories:
- Generative AI
- ChatGPT
- Token
- Prompt Engineering
date: 2023-07-19
---



Thanks to Andrew Ng's prompt engineering course, I summarize some writing principles for preparing a prompt to ChatBot.



A holistic prompt should inludes3 types of content



1. The role that you want Chatbot to work as

2. Task Setting and the direction you want to want on with

   a. Specific Task description, which involves procedures

​		b. An Example

3. Hints, such as output requirement etc



Example:

```python
'''
[Role] Hi Chatbot! 

You are a professional Mechine Learning Engineer, specialize in entity recognition, text summarization, and are proficient in incontext-learning.

[Task]

      Your task: extracting entities from the artical below, and then summary the article content, then evaluate your summary

[Procedure]

      1、Go throught the artical and fully grasp the theme, style, and key information of the text

      2、Extract named entities, such as time, place, characters and other key information

      e.g ['Charlie', 'London', 'Watching Movie', 'Lake District' ]

      3、Do the text summary, do not lose the key information

      4、Score the quality of the text summary

[Hints]

1. Evaluation score should be from 1 -10
2. Output data should be in Json format

'''
```

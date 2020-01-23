---
layout: post
title:  "BERT dictionary - word embedding"
date:   2020-01-19 15:35:08 -0500
categories: jekyll update
---
The topic of the day: **BERT (Bidirectional Encoder Representations from Transformers)** is huge(and popular) NLP library. Apparently it can perform many language tasks, and I don't understand but am still learning how it works. A first reasonable step is to see how it handles the fundamental parts of a given language - what is the first tool you would need when study a new language (say it's new to you, but not new to the native speakers)? A dictionary.

When Neural Network (what BERT is based on) learns a language/text, it needs a dictionary too. The difference is that human dictionary puts words together by some alphabetical orders, while NN dictionary puts the words has the similar meanings together. The longer distance between the two words, the more un-relatable the words are to each other. This kind of dictionary for NN, it is called **Word Embedding**.

One might ask "alright it's cool that you put word with similar syntactic meanings together, but how do you find a word in this mass Word Embedding pool?" Yes, it still needs a way to find individual word. This is a Word Embedding look-up table, a data structure to give every word a unique ID.

BERT has about 30,000 tokens in its tokenizer class. Each token has 368 features, which means a vector 368 dimensions for representing a word. These are the basic information about BERT, and not some magic number that the universal tells us 368 dimensions how we should represent a word by fate.

BERT is pre-trained, and its vocabulary is fixed. Sounds less powerful? But when it sees a new word, it will break it into several subwords (sometimes called morphemes) or individual letters for worst case. Chris McCormick showed in his tutorial that it is not the case that the subwords are necessarily existing in the fixed vocabulary, so this leaves us to think how BERT subwording works.

My learning source is from [ChrisMcCormickAI].

[ChrisMcCormickAI]: https://www.youtube.com/watch?v=zJW57aCBCTk&t=4s

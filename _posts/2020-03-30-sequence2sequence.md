---
layout: post
title: "Some terms in Sequence2Sequence model"
date:   2020-04-30 00:04:04 -0500
categories: jekyll update
---

**A language model** can generate sentences and can also give you a probability of a sentence.

**Machine translation (MT)** includes **encoded network** and **decode network**. The decoding part is like a regular language model. The encoding part is a bit more complex with the input which contains a language modal whose probabilities are based on the condition of another language. That's why an MT algorithm can be called a *conditional language model*.

**Greedy search** in MT is to find the best first word and the best second word does not perform well.

**Bleu (BiLingual Evaluation Understudy) score** is a conventional system built for evaluating MT result with using precision. It's designed to generate *the best* translation for every input so that we won't get an overwhelmingly long list of possible translations for one sentence.

**Precision used in Bleu** as long as the word is the most frequent word occurs in the input language. A translation of `The the the the the.` will make Bleu happy.

**Modified Precision** Do some caring work by taking the positions of the words into consideration.

The difference between the two precision is how to count the occurrence of the target phrase in the reference candidates. *count* versus *clip count*

Philosophic question: What are the possible ways to find the best translation among candidates. BiLingual Evaluation Understudy is a humble name that acknowledges that itself is not perfect.  

The wisdom of Bleu is that it allows trying out different ideas to find the *best* MT output and return a raw number to give a systematic score of the output -- a groundbreaker for the endless unmeasurable argument of what should be the best. Again, it is not perfect.

**BP (bevery penalty)** gives the penalty to the output whose length is shorter than the one of the references.

**Long sequence problems** Bleu score will get lower when the sentence is very long, from 20 words-ish above. I guess the reason for this is how the modified precision is calculated -- when the denominator is bigger (more words) and the pairs of phrases grouped by n-grams are hard to be found in the reference sentences.

**Attention model** RNN forward network and attention weight are involved. The design is trying to tell for every output word, which part of the other sentence in the language we should pay attention to.  

In the beginning, I questioned what kind of improvement attention modal is making better than Bleu. Then now I realized that this is an invalid question because the Bleu score is dealing with the scoring for output, and attention model attempts to gather more information on the relationship between a translation pair of two languages. Since we know that the Bleu score becomes a little unreliable for longer sentences, we will lose some accuracy feedback for those sentences. Without a valid scoring system, we should try our best to use our own way to make a better translation. An analog of this is more or less like a student and teacher relationship. If the only job a teacher can do is to give a score for student homework and exams to provide a performance evaluation of the student progress, then the student will feel lost if the grades are longer serves an accurate measurement for the learning progress. The attention model is that instead of panic, the student study even harder, and starting improve self-learning skills to be a better learner who doesn't need to rely on a teacher's grade to get a sense of the learning process. Isn't it?

**The gates in LSTM** uses the sigmoid function which tracks long-distanced dependency: Activation Gate at each time step, State Gate.

**clipping** clipping function is built to avoid vanishing (too low) and exploding (too high) gradients, which happen during back propagation.

**Concatenation**

```python

# Concatenate a_prev and xt (≈1 line)
concat = np.concatenate((a_prev,xt), axis = 0)

```

I learned my knowledge from [Deeplearning.ai] by Andrew Ng.

[Deeplearning.ai]:https://www.youtube.com/watch?v=smHa2442Ah4&list=PLkDaE6sCZn6Gl29AoE31iwdVwSG-KnDzF&index=4

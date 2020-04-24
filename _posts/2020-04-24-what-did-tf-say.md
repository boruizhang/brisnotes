---
layout: post
title:  "What did TensorFlow say?"
date:   2020-04-24 00:15:15 -0500
categories: jekyll update
---

*This is a collection of random thoughts on TensorFlow for AI (last update April 24)*

**Too much epochs** can cause overfitting too.

**Relu** seems to be magic hidden layer activation function.

**Normalizing** is to get the values between 0 and 1, and `Python` does a great job on this with one simple line without looping.

**Callback function** let the training stop epoching once reaches the ideal loss.


```python
class myCallback(tf.keras.callbacks.Callback):
  def on_epoch_end(self, epoch, logs={}):
    if(logs.get('loss')<0.2):
      print("\nReached 80% accuracy. Stop training and save the electricity!")
      self.model.stop_training = True
```
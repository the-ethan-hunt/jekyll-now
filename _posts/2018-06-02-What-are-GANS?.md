---
layout: post
title: What are GANS?
---

It's been a really long time since I have written something here. In fact, it's been long since I have worked in open source.
After the GSoC results came and I was not selected, I decided to take a break from open source. Since I also had my end semester 
exams at the same time, I could make it a nice excuse to tell people why I suddenly took a break. The excuse cover was really good!

However, in the last few days with practically nothing to do, I have tried to set myself back on the open source bandwagon. More
precisely, the deep learning community. I have been working on Generative adversarial nets(it's not that nerdy as it sounds!) and
decided to write about it in my post.

## What's a GAN?

Yann LeCun wrote [an answer](https://www.quora.com/What-are-some-recent-and-potentially-upcoming-breakthroughs-in-unsupervised-learning)
on Quora where he said that "Adversarial Training is the coolest thing since sliced bread". No offense intended to Prof. LeCun but he 
probably forgot stuff like Hot Chili sauce or spices or the coming of Torch that has affected the deep learning community.

When you google "GAN in simple english", you come across a Wikipedia page about a language spoken in China. We are not going to talk 
about that, of course. But I might be able to explain to you in simple terms about what is a GAN.

Suppose you have a picture of yourself; you sipping a Virgin Bloody Mary at a pool wearing Ray-Ban glasses. You brag about it to your
friends after the vacation gets over, adding a garnishing that this was Bali or Goa( I love both!). One of your eagle-eyed friend who's
probably watching a lot of Sherlock however makes it clear that the pool and the Mary were photoshopped. When such stuff happens with 
neural networks, it's called a discriminative model. A discriminative model determines whether a picture is natural or has been created 
artificially. In this context, being natural is whether it belongs to the dataset of the network.

Coming back to the main idea, another friend of yours has got your back. He helps you produce another similar photo of yourself, this time 
you are drinking tequila shots. This friend of yours is a generative network. A generative network tries to create a natural image similar
to the original data. For people who teetotal like me, get this straight: a generative network is North Korea(See [this article from the 
Telegraph](https://www.telegraph.co.uk/news/2017/12/11/quality-fake-supernotes-found-seoul-fan-suspicions-north-korea/)) and the
discrinative model is the FBI.

## Deeper into the deep learning aspect

The first thing a discriminator does is to look for the obvious stuff that separates a real image from a fake one. By training,
the discriminator learns more and more and so does the generator. In fact, the generator takes advantage of what the discriminator
learns in order to learn for itself. This continues for millions of iterations. The dicriminator learns more and more subtle ways to 
differentiate while a generator learns new moves to create a fake one.

With enough training, the generator finally makes fakes seem so real that even we humans are not able to distinguish them.

## Implementing the GAN( fun ends here; hell starts here)

Let's get a little serious now(you had been warned!). The generator(G) and discriminant(D) are feed-forward neural networks. The generator
takes an input of vector of random numbers(z) and transforms it into a data it intends to copy. The discriminator takes a set of data
as input and determines the probability whether it is real or not. Both functions are alternatively optimised on batches of real and 
generated data until the GAN will slowly converge to producing realistic data; almost as realistic as modelling it.

GANs are getting hot for image generation using convolutional neural networks. A [DCGAN](http://arxiv.org/abs/1511.06434) or a deep convolutional
generative adversarial network is one great GAN used for image generation. You can read the paper in the link to know more about them. 

I hope you like this post and that this post would quell you to learn more about GANs or about deep learning itself!


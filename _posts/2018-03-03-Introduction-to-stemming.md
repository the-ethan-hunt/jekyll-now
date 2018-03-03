---
layout: post
title: Introduction to Stemming
---

Stemming can be regarded as an important primeval process in Natural Language Processing. The main purpose of 
stemming is to reduce a verb, adjective or an adverb to its root form. For example, the stem of 'swimming','swims','swim' is 'swim' only.
Similarly, 'training','trains','trained' all have the same root word: 'train'. As a result stemming is regarded as an important process in 
lexicon normalisation.
The popular NLP library [NLTK](http://www.nltk.org/) uses Stemmer ( a Porter stemming algorithm, we will learn about this in detail)
as a feature too.

``` 
 In[1]: from nltk.stem.porter import PorterStemmer

 In[2]: stem=PorterStemmer()

 In[3]: word="swimming"`

 In[4]: stem.stem(word)`

 Out[4]: 'swim'
 ```
 
 We are going to discuss some particular stemming algorithms and how they work actually in this post.
 
 ## Porter Stemmer
 
 The Porter stemming algorithm is one of the most popular stemming algorithms. The base concept is most of the suffixes in English language 
 are made up of smaller suffixes. It has five steps, and within each step, rules are applied until one of them passes the conditions. 
 If a rule is accepted, the suffix is removed accordingly, and the next step is performed.
 
 For example, a rule (m>0) EED → EE means “if the word has at least one vowel and consonant plus EED ending, change the ending to EE”.
 So “agreed” changes to "agre" while "feed" does not change. The algorithm has implementations in several other languages like Turkish, French 
 and Spanish to name a few.
 
 Although fairly accurate, the Porter algorithm has a lower data reduction than other algorithms thus decreasing its speed.
 
 ## Lovins stemmer
 
 Proposed by Lovins in 1968, this algorithm performs a lookup on a table of 294 endings, 29 conditions and 35 transformation rules,
 which have been arranged on a longest match principle. The algorithm then removes the longest suffix from a word and then recodes it 
 using another table to convert the stem into valid words.
 The biggest advantage of this algorithm can be regarded as it can handle irregular plurals like 'index' and 'indices' or 'dice' and 'die'.
 But the algorithm is time and data consuming and is not as accurate as the former one.
 
 ## Paice-Husk Stemmer
 
 It is an iterative algorithm with one table containing about 120 rules indexed by the last letter of a suffix. With every iteration, it
 tries to find a rule by the last character of a word. It also terminates if a word starts with a vowel and there are only two letters
 left or if a word starts with a consonant and there are only three characters left.
 
 It is a very simple algorithm with both deletion and replacement being taken care by iterations. However, there is a huge chance that
 overstemming may occur.
 
 ## N-Grams stemmer
 
 This stemmer uses statistical analysis for stemming. An n-gram is a set of n consecutive characters extracted from a word. Like the word
 "calling"  is to be split in bigrams(n=2), it can be "*c","ca","al","ll","li","in","ng","g*" that is 6 bigrams. It can be thus said that
 for an n characters, there are 2n-1 number of n-grams in the word.
 
 N-grams is language independent and hence quite useful in several applications. The disadvantage can be said that it's very time-consuming.
 
 ## HMM stemmer
 
 Short for "Hidden Markov Model", which are finite-state automata where transitions between states are ruled by probability functions. At 
 each transition, the new state emits a symbol with a given probability. The probability of each path can then calculated and the most 
 probable path can be found out by [Viterbi algorithm](https://en.wikipedia.org/wiki/Viterbi_algorithm).
 
 Before applying HMMs following assumptions are to be taken care of:
 - Initial states belong only to the stem-set - a word always starts with a stem
 - Transitions from states of the suffix-set to states of the stem-set always have a null probability - a word can be only a
   concatenation of a stem and a suffix. 
 - Final states belong to both sets - a stem can have a number of different derivations, but it may also have no suffix.
 
 The states are divided into two disjoint sets with one only stems and the latter suffixes and stems. For any given word, the most probable
 path from initial to final states will produce the split point (a transition from roots to suffixes). Then the sequence of characters 
 before this point can be considered as a stem.
 
 The advantage of this algorithm is that it does not require a prior linguistic knowledge. But it is a little complex and there might be
 a danger of overstemming.
 
 
 There are some more stemming algorithms like YASS, Krovetz and Xerox but they are either a little complicated or they apply to only one domain.
 the above-mentioned ones were among the most popular ones used today and it was very interesting for me to explore them and record their
 advantages and disadvantages.
 
 
 
 
 
 
 
 
 
 
 
 

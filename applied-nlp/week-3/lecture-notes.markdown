# Document Classification

A binary classifier takes a document and classifies it into two classes,
ie to determine a good or bad review

A multi-class classification can produce a number of different classifications, multi-class classifiers
can often be described as multiple binary classifiers

## General Issues
- Specifying what makes a document in one class or another, 
can we learn from the positive / negative examples to improve prediction
- Adapting to dynamics of data source
- Unbalanced classes
- Is one decision per document appropriate?

## Beyond classification
- Identification of parts of a document which are relevant or where sentiment is expressed.
- Identification of specific entities within a document that sentiment (or other classification) may be applied to

## Words as features
- Words within documents provide excellent evidence of being in a particular class
    - excellent, indication that a review is positive
    - viagra, indication that an email is spam
    - lemma, evidence that an article is relevant to NLP
- KEY IDEA: Just treat a document as a bag-of-words, ignoring grammatical structure
    - Sometimes ignore frequency, but this would be called a set-of-words

## Feature representation
May be binary-values:
    - D1 = {cats: True, mice: True ...}
Or real-values:
    - D2 = {cats: 1, mice: 1, chase: 1, the: 2}
  
Might be stored with sparse vector representation such as python dictionaries (as above)
    - Default value for keys not present is False / zero

## Scoring documents
- A document is treated as a bag-of-words, d
- Number of occurrences of word w in d is denoted:
    `count(d,w)`
- Generalise to total occurrences of words from L in d

### Options
- Frequency
- Uniform score for occurrence
- Weighted by 'importance' of word


## Automatic derivation of wordlists
Use a sample of labelled documents
- Need to ensure that both (all) classes are represented in sample
- Class imbalance can be a big problem

Partition this into training and testing sets
- Common splits are 50:50, 80:20 and 90:10

Use this training set to build a model

## Learning classifiers
### Naive bayes classification
P(c|f<sub>1</sub><sup>n</sup>) = 
argnax P(f<sub>1</sub><sup>n</sup>).P(c) / P(f<sub>1</sub><sup>n</sup>)

or 

argnax P(f<sub>1</sub><sup>n</sup>).P(c)

What is the probability that of having a set of features, f<sub>1</sub><sup>n</sup> given class of type c

### Naive parameters
- Prior probabilities:
```
P(f|c)
```
- The conditional probabilities of each feature given each class:
```
P(c)
```

There are 3 documents containing the word fabulous. 
Two of these documents are labelled positive and 1 of them is labelled negative. 
Given that there are a total of 40 positive documents and 60 negative documents, 
what is P("fabulous"|positive)?

2 / 40 = 0.05

## Smoothing
- Nothing is impossible!
- We need to smooth the estimated probability distributions
- The simplest form of smoothing is **add-one** smoothing
- Simply add one to all of the counts when estimating P(f|c)
    - So if we haven't seen a feature with class give it a count of 1
    - If it has been seen once, it now is 2 etc.
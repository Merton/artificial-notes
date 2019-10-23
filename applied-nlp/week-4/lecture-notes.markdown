# Document Classification
## Evaluating classifiers
We need a labelled dataset that has not been used in training

To evaluate the classifiers we can use accuracy and error rates, but these are prone 
to being misleading if we have an unbalanced ratio of classes in the data.

Using a confusion matrix means you take into account the true and false positives / negatives.
We can calculate Precision, the properotion of +ve predictions that are correct:
```
Precision = TP / TP + FP
```

Recall is the properotion of actually +ve documents that are predicted correctly
```
Recall = TP / TP + FN
```

In general we want high precision AND high recall, we can combine precision and recall
using the **F1-score**.

```
F1 = 2PR / P + R
```

### Trading off Precision and Recall
FOr any given classifier, we can change the decision boundary, making it more or less
likely to classify an item as positive.

Naive bayes decision rule

# Document Similarity 
We can model our documents in vector space, allowing us to compare a document to one another 
based on their position in space. Each term represents its own dimension in space, so we will end up with
a very high dimension model.

## Measuring term value
- Weight or value of a term should reflect importance in document
- Term Frequency
    - More frequent terms may be more important
    - But high frequency words are not always discriminating
        - E.g., stop-words
        - The term “country” in a collection of documents about travel
- Document Frequency
    - Terms which occur in less documents may be more important
    - The term “Kenya” in 3 documents in a collection of documents about travel, this conveys a lot about the context even though
    there is only 3 occurrences
    
## Term Frequency Inverse Document FREQUENCY (TF-IDF)
Term frequency is the number of occurrences of a term in a document:
```
tf(d, t)
```

Document frequency is the number of documents in which a term occurs:
```
df(t)
```

If there are N documents in total, inverse document frequency is given by:
```
idf(t) = log⁡(N/df(t))
```

Term frequency inverse document frequency:
```
tf−idf(d,t) = tf(d,t)×idf(t)
```


## Vector Similarity 
Similar items are close together in the vector space, with dissimilar items being further away

We can use euclidean distance or cosine similarity to determine this closeness

The cosine similarity is the angle between the two vectors, can be calculated:

```
sim(d1,d2) = cos(theta)
           = a.b / sqrt(a.a x b.b)
```
(where . is the dot product)

## Beyond words as dimensions
So far we have assumed that topic terms are unigrams (single-words)
Often a phrase or multiword term is characteristic of a topic:
    - n-grams
    - eg, "hedge fund", "black hole"
    - Individual words may be ambiguous or too general

## Collocations
A collocation are n-grams which occur together more often than by chance

Consider a bigram "black hole", we need to determine how often the bigram occurs and how often each
of the individual terms occur, to see if the bigram is more frequent.

## Point=wise mutual information (PMI)
The probabilty of the n-gram, divided by the probability of each term multiplied:

PMI(w<sub>1</sub>, w<sub>2</sub>) = log(P(w<sub>1</sub>, w<sub>2</sub>) / P(w<sub>1</sub>) x P(w<sub>1</sub>)

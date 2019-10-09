# Text Processing
## Document retrieval scenario
A corpus is a collection of documents, which might be: 
- News articles,
- Essays,
- Books,
- Web pages
- Tweets

Given a corpus, humans automatically intelligently break it down (or segment) it into meaningful units

- Documents
- Paragraphs
- Sentences
- Words
- Morphemes and or syllables
- Characters

Given a corpus computers automatically see
- A sequence of characters
- Represented as a sequence of zeroes and ones

## Document representation
How do we represent collections of documents efficiently?

- Document and sentence segmentation; what makes a document and sentence
- Word tokenisation
- Text normalisation (case, numbers, stopwords, punctuation)
- Stemming / lemmatisation (cat == cats)
- Generation of "bag-of-words" representation, a set of words, ignoring frequency and order
- Indexing (word -> [document ids])

## Segmentation and lemmatisation
First document segmentation to collate and organise your corpus

Segmenting sentences by standard features like Capitilisation, punctionation is not very robust due to incorrect use of punctuation, and it is often very ambiguous

Advanced sentence tokenization methods work by building a binary classifier to decide whether a full stop is part of the word or is a sentence-boundary marker.
It may be based on a sequence of rules or machine learning. It helps to have a dictionary of commonly used abbreviations.

## Tokenisation
- Task of segmenting running text into "words"
- Tokens might actually be: 
    - Words
    - Items of punctuation
    - Numerical quantities
- Tokens can contain whitespace

We could use python's String split() function in a very simple cases, we can write and use regex for more complex splitting. Or we can use the NLTK regex tokeniser for prebuilt functionality.

How you could use regex and splot to tokenise a sentence in Python:
```python
re.sub("([.?!'])", " \g<1>", "I'm going home!").split()
```

For tokenisation in other languages we can use a simople approach which is a greedy search called **maximum matching** or sometimes **MaxMatch**.

**Types** are the number of unique types of tokens in a corpus.
As the size of the corpus increases, the number of word types increases.

## Zipf's Law

Herdan-heads law averafe type frequency in 1M words is 30.
Frequency distribution of word types is not uniform or even normal - It's _Zipfian_!

Half of the types will be **hapax legomena**, meaning they occur only once.

If the most frequent term appears 100 times, the second would appear 50, third 33 etc.

## Normalisation
### Case Normalisation 
In some applications (speech recognition) case isn't available.
In others, lower and upper case distinctions are often considered irrelevant.

Advantages of ignoring case:
- reduces the number of types to consider
- Increases the frequency of each type

Disadvantages of ignoring case:
- Increases problem of ambiguity, eg, where case is used to indicate a name

### Number normalisation
An infinite amount of numbers, which all count as a new token.

In many applications, the exact number is irrelevant, so commonplace to replace numbers with a generic string like NUM.

 
### Rare words
 Might be names, scientific or spelling errors. We typically ignore rare words by checking their frequency or only consider top n most frequent words.

### Punctuation and stopword removal
The most common words in English tend to be non-content bearing function words, also known as **stopwords**.

## Stemming and Lemmatisation
When you search for cats, you probably want results containing both 'cat' and 'cats'.

Morphology is the study of the way words are made up of smaller parts.

### Inflectional morphology
| category | distinction | Example |
| ------- | --------| -----|
| number | singular vs plural | cat vs cats |
| gender | masculine vs feminine | bleu vs bleue |
| tense | Present vs past vs future | love vs loved | 
| person | 1st vs 2ns vs 3rd | I am vs you are vs he is |
| case | Nominative vs accusative vs dative | Mark's vs Marks'|

### Derivational morphology
Process of creating or deriving a new word from an existing word using affixes

It adds substantial new mean often a different part of speech.

For example: 
- start (VERB)
- starter (NOUN)
- restart (VERB)
- restartable (ADJECTIVE)

Less clear that we want to ignore distinctions (even in search applications). But by analysising derivational morphology can help us to understand
previously unseen words.


### Stemming

Stemming removes unwanted affixes, ie:
 - relational -> relat
 - relate -> relat
 - hopeful -> hope
 - caresses -> caress
 - organisation -> organ (Hmmm!)
 
 It does not require a dictionary, but can result in non-words or incorrect roots.

### Lemmatisation
Replaces word with dictionary head word

Requires a lexicon or dictionary, and uses knowlesdge of inflectional morphology.

Works by applying stemming rules and comparing results to WordNet dictionary. 
If result is a real word, keep it, else use original word.
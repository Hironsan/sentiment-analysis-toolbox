# Sentiment analysis toolbox

In this project, you can quickly perform sentiment analysis on some datasets such as Tweets, movie review and so on since all of the codes are on Jupyter Notebooks.
Also, there are various methods such as SVM, Multinomial Naive Bayes, Convolutional Neural Network and so on.

## Table of contents

1. Basic Text Pre-processing
* Tokenization
* Text Normalization
  * Casing characters
  * Replacing numbers
  * Stemming
  * Lemmatization
  * Spelling correction
* Removal
  * Punctuation removal
  * Stopwords removal
  * Frequent words removal
  * Rare words removal

## Text Pre-processing

### Tokenization

Tokenization is the process of taking a text or set of texts and breaking it up into its individual words. In this step, we will tokenize text with the help of splitting text by space or punctuation marks.

A text can be split into words using the function `word_tokenize` in `nltk.tokenize` module:

```python
>>> from nltk.tokenize import word_tokenize
>>> s = '''Good muffins cost $3.88\nin New York.  Please buy me
... two of them.\n\nThanks.'''
>>> word_tokenize(s)
['Good', 'muffins', 'cost', '$', '3.88', 'in', 'New', 'York', '.',
'Please', 'buy', 'me', 'two', 'of', 'them', '.', 'Thanks', '.']
```

NLTK has a tokenizer for tweets:

```python
>>> from nltk.tokenize import TweetTokenizer
>>> s = '@remy: This is waaaaayyyy too much for you!!!!!!'
>>> word_tokenize(s)
['@', 'remy', ':', 'This', 'is', 'waaaaayyyy', 'too', 'much',
 'for', 'you', '!', '!', '!', '!', '!', '!']
>>> t = TweetTokenizer(strip_handles=True, reduce_len=True)
>>> t.tokenize(s)
[':', 'This', 'is', 'waaayyy', 'too', 'much', 'for',
 'you', '!', '!', '!']
```

For further detail, see [nltk.tokenize package](https://www.nltk.org/api/nltk.tokenize.html).

### Text Normalization

Text normalization is the process of transforming text into a single canonical. Normalizing text before processing it ensure that these words are consistent. For example, converting character case or stemming words:

* Casing characters
* Replacing numbers
* Stemming
* Lemmatization
* Spelling correctioin

#### Casing characters

#### Replacing numbers

#### Stemming

Stemming  algorithms  work  by  removing the suffix of the word, according to some grammatical rules.  In this  study, we  apply  the Snowball  stemmer library2,  which  is  the  most  popular  and  standard approach. 

2 http://snowball.tartarus.org/ 

#### Lemmatization

#### Spelling correction

### Removal

* Filtering
* Punctuation removal
* Stopwords removal
* Frequent words removal
* Rare words removal

#### Filtering

Filtering is nothing but cleaning of raw data. In this step, URL links (E.g. http://twitter.com), special words in twitter (e.g. “RT” which means ReTweet), user names in twitter (e.g. @Ron -@symbol indicating a user name), emoticons are removed.

#### Stop words removal

Stop words removal is the process of eliminating stop words from text. Stop words are words which are filtered out before or after processing of text. For example, "a", "the", "is", "of", etc... are stop words. Stop words are meaningless and useless for the sentiment analysis. This process reduces the corpus size.

Stop words can be filtered by using `stopwords` in `nltk.corpus`:

```python
>>> from nltk.corpus import stopwords
>>> from nltk.tokenize import word_tokenize
>>> 
>>> s = 'This is a fantastic movie!'
>>> stop_words = stopwords.words('english')
>>> words = word_tokenize(s)
>>> words
['This', 'is', 'a', 'fantastic', 'movie', '!']
>>> [w for w in words if w not in stop_words]
['This', 'fantastic', 'movie', '!']
```

<!--
http://www.cs.cmu.edu/~mccallum/bow/rainbow/ 
-->

## Reference

* [Sentiment analysis of reviews: Text Pre-processing](https://medium.com/@annabiancajones/sentiment-analysis-of-reviews-text-pre-processing-6359343784fb)
* [Ultimate guide to deal with Text Data (using Python) – for Data Scientists & Engineers](https://www.analyticsvidhya.com/blog/2018/02/the-different-methods-deal-text-data-predictive-python/)
* [A Comparison between Preprocessing Techniques for Sentiment Analysis in Twitter](http://ceur-ws.org/Vol-1748/paper-06.pdf)
* [Data Preprocessing, Sentiment Analysis & NER On Twitter Data.](http://www.iosrjournals.org/iosr-jce/papers/Conf.17014-2017/Volume-2/15.%2073-79.pdf?id=7557)
* [The effect of preprocessing techniques on Twitter sentiment analysis](https://www.researchgate.net/publication/311755864_The_effect_of_preprocessing_techniques_on_Twitter_sentiment_analysis)
* [Preprocessing text before use RNN](https://datascience.stackexchange.com/questions/11402/preprocessing-text-before-use-rnn)
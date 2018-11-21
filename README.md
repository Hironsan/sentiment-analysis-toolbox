# Sentiment analysis toolbox

In this project, you can quickly perform sentiment analysis on some datasets such as Tweets, movie review and so on since all of the codes are on Jupyter Notebooks.
Also, there are various methods such as SVM, Multinomial Naive Bayes, Convolutional Neural Network and so on.

## Table of contents

1. Basic Text Pre-processing
* Tokenization
* Text Normalization
  * Normalizing case
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

* Normalizing case
* Replacing numbers
* Stemming
* Lemmatization
* Spelling correctioin

For further details, see [CS506/606: Txt Nrmlztn](http://www.csee.ogi.edu/~sproatr/Courses/TextNorm/).

#### Normalizing case

Normalizing case is the process of transforming characters into the same case. This process ensures that the same words are recognised as the same. In this case we transformed into lowercase:

```python
>>> s = 'The Da Vinci Code was REALLY good.'
>>> s.lower()
'the da vinci code was really good.'
```

We can also lower text after tokenization:

```python
>>> from nltk.tokenize import word_tokenize
>>> s = 'The Da Vinci Code was REALLY good.'
>>> words = word_tokenize(s)
>>> words
['The', 'Da', 'Vinci', 'Code', 'was', 'REALLY', 'good', '.']
>>> [w.lower() for w in words]
['the', 'da', 'vinci', 'code', 'was', 'really', 'good', '.']
```

#### Replacing numbers

#### Stemming

Stemming is the process of reducing inflected words to their word stem. For example, "listen", "listened", "listening" are reduced to the same stem "listen". Some application like sentiment analysis can benefit from stemming because it reduces vocabulary and increase the relevance of the concept.

For stemming, we can use `SnowballStemmer` in `nltk.stem.snowball`:

```python
>>> from nltk.stem.snowball import SnowballStemmer
>>> st = SnowballStemmer('english')
>>> st.stem('running')
'run'
>>> st.stem('greatly')
'great'
```

There are other stemming algorithms in NLTK. For further information, see [nltk.stem package](http://www.nltk.org/api/nltk.stem.html).

#### Lemmatization

Lemmatization is the process of grouping together the inflected forms of a word so they can be analysed as a single item, identified by the word's lemma, or dictionary form. For example, "am", "are", "is" are lemmatized to the same form "be".

For stemming, we can use `WordNetLemmatizer` in `nltk.stem.wordnet`. Before we use the lemmatizer, we should download WordNet:

```python
>>> import nltk
>>> nltk.download('wordnet')
```

Now, we are ready to lemmatize word:

```python
>>> from nltk.stem.wordnet import WordNetLemmatizer
>>> lt = WordNetLemmatizer()
>>> lt.lemmatize('am', pos='v')
'be'
>>> lt.lemmatize('are', pos='v')
'be'
>>> lt.lemmatize('is', pos='v')
'be'
```

#### Spelling correction

### Removal

* Filtering
* Punctuation removal
* Stopwords removal
* Frequent words removal
* Rare words removal

#### Filtering

<!--
Filtering is nothing but cleaning of raw data. In this step, URL links (E.g. http://twitter.com), special words in twitter (e.g. “RT” which means ReTweet), user names in twitter (e.g. @Ron -@symbol indicating a user name), emoticons are removed.
-->

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
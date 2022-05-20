---
title: "Python Text Analysis"
teaching: 0
exercises: 0
questions:
- "What else can we do with our tweets?"
- "How can I analyze my tweets beyond what twarc offers?"
- "Is it possible to tell if tweets are expressing positive or negative feelings?
"


objectives:
- "We use Python and the power of Pandas with our Jupyter notebook"
- "Sentiment analysis measures the 'positivity' or 'negativity' of language"

---

# 

ep 6 objective?
- "twarc1 .py utilities and twarc2 plug-ins are two separate sets of tools"

# Where we've been: twarc built-ins
We have already looked at the proportions of tweets to retweets,
and examines Emojis as a proxy measurement of qualitative emotional 
content. ie: you can visually see sentiment in emojis.

The are emotional icons.

# Sentiment Analysis with TextBlob
Sentiment analysis can be used to estimate the overall 
positivity or negativity of a text corpus. There are a variety 
of algorythms and scales. TextBlob's default `.sentiment` 
function rates an input text as negative or positive on a 
scale of -1 to 1.

TextBlob is a Python library that does all sorts of text
processing. 

Before we can do any sentiment analysis, we need to download
the linguistic datasets that TextBlob uses in its analyses:

~~~
!python -m textblob.download_corpora
~~~
{: python}

We need to feed TextBlob something like plain text. Therefore, 
we need to create a text object from out dataframe. 
That column is named `text`, we pull that  
out of our dataframe and convert it to a list. Then we can 
convert the list into one long string. 

We can do this all in 
one line of code.

#FIXME 
Describe the algorhythm and a little bit about what else it does,
like remove stop words and url's, determines language, etc.

TextBlob requires its own special datatype, so we convert our 
string into a blob. Then we send the blob through TextBlob's
sentiment method.

~~~
# break tweets test column into a list, 
# then .join into one long string 
kittens_string = ' '.join(kittens_df['text'].tolist())

# turn the string into a blob
kittens_blob = TextBlob(kittens_string)

# get the sentiment
kittens_blob.sentiment
~~~
{: .python}

~~~

~~~ 
Sentiment(polarity=0.4313034129204853, 
subjectivity=0.7558201654919634) 
~~~ 
{: .output}

The overall sentiment of the language of our kittens tweets is rather 
positive. And the tweets tend to be subjective.



Challenge: Anticipating sentiment

Write Python code that outputs three sets of 
sentiment values:  taxday, catsofinsta, capitolriotsrehydrated

When you output the three values, arrange them in what you guess
will be the least positive to most positive sentiment.




What else from the old slide-deck must we cover?
Twarc2 extensions
Network (very slow. Demo only? Pre-worked example?)



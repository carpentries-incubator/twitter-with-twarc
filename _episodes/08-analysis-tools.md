---
title: "Analysis Tools"
teaching: 0
exercises: 0
questions:
- "What else can we do with our tweets?"
- "How can I analyze my tweets beyond what twarc offers?"
- "Is it possible to tell if tweets are expressing positive or negative feelings?
"


objectives:
- "twarc1 .py utilities and twarc2 plug-ins are two separate sets of tools"
- "We use Python and the power of Pandas with our Jupyter notebook"
- "Sentiment analysis measures the 'positivity' or 'negativity' of language"

keypoints:
- "What else? (FIXME)"
---

# 

Twarc utilities
We already did tweets/retweets
Pull out Emojis only?
  you can visually see sentiment there.
What else from the old slide-deck must we cover?
Twarc2 extensions
Network (very slow. Demo only? Pre-worked example?)

# Sentiment Analysis with TextBlob
Sentiment analysis can be used to estimate the overall positivity or
negativity of a text corpus. There are a variety of algorythms and scales. 
TextBlob's default `.sentiment` function rates an input text as negative or
positive on a scale of -1 to 1.

TextBlob is a Python library that does all sorts of text
processing. 

Before we can do any sentiment analysis, we need to download
the linguistic datasets that TextBlob uses in its analyses:

~~~
!python -m textblob.download_corpora
~~~
{: code}

We need to feed TextBlob something like plain text. Therefore, we need 
to create a text object. So we take the text column out of our dataframe 
and convert it to a list. Then we can convert the list into one long 
string. We can do this all in one line of code.

XXX Describe the algorhythm and a little bit about what else it does,
like remove stop words and url's, determines language, etc.

TextBlob requires its own special datatype, so we convert our 
string into a blob. Then we send the blob through TextBlob's
sentiment method.

~~~
# break tweets test column into a list, then .join into one long string 
kittens_string = ' '.join(kittens_df['text'].tolist())

# turn the string into a blob
kittens_blob = TextBlob(kittens_string)

# get the sentiment
kittens_blob.sentiment
~~~
{: .source}

~~~

~~~
Sentiment(polarity=0.4313034129204853, subjectivity=0.7558201654919634)
~~~
{: .output}

The overall sentiment of the language of our kittens tweets is rather 
positive. And the tweets tend to be subjective.





Challenge: sentiment of taxday.jsonl
Do you think the se

---
title: "Python Text Analysis"
teaching: 15
exercises: 20
questions:
- "What else can we do with our tweets?"
- "How can I analyze my tweets beyond what twarc offers?"
- "Is it possible to tell if tweets are expressing positive or negative feelings?"

objectives:
- "We use Python and the power of Pandas with our Jupyter notebook"
- "Sentiment analysis measures the 'positivity' or 'negativity' of language"

---

## Where We've Been: twarc Built-ins
We have looked at the hashtags in a dataset, the
proportions of tweets to retweets, and the networks of users created
by a tweet-stream. But what about content
of the tweets? For that we need some textual analysis, and so far all
we've done is count words.

# Sentiment Analysis with TextBlob
TextBlob is a Python library that does all sorts of text processing, 
including sentiment analysis. 

Sentiment analysis can be used to estimate the overall 
positivity or negativity of a text corpus. There are a variety 
of algorythms and scales. TextBlob's default `.sentiment` 
function rates an input text as negative or positive on a 
scale of -1 to 1.

The sentiment function returns two numbers in the form of a named tuple: 

Sentiment(polarity, subjectivity). 

The polarity score is a float 
within the range [-1.0, 1.0]. Subjectivity is a float within the 
range [0.0, 1.0] where 0.0 is very objective (ie: does not express
strong sentiment) and 1.0 is very 
subjective.

Before we can do any sentiment analysis, we need to download
the linguistic datasets that TextBlob uses in its analyses:

~~~
!python -m textblob.download_corpora
~~~
{: python}

We need to feed TextBlob something like plain text. Therefore, 
we need to create a text object from our dataframe.
 
That column is named `text`, we pull that 
out of our dataframe and convert it to a list. Then we can 
convert the list into one long string. 

TextBlob wants to get fed a string, so we will give it a string and convert that 
string into a blob. Then we send the blob through TextBlob's sentiment method.


We can do this all in one cell, or one cell at a time to make
sure we don't have any mistakes.


~~~
# break tweets text column into a list, 
# then .join into one long string 
hashtagcats_list = ' '.join(hashtagcats_df['text'].tolist())
# turn the string into a blob
hashtagcats_blob = textblob.TextBlob(hashtagcats_list)
# get the sentiment
hashtagcats_blob.sentiment
~~~ 
Sentiment(polarity=0.2378257657037288, 
          subjectivity=0.6328352645350159)
~~~ 
{: .output}
{: .python}


The overall sentiment of the language of Cat Twitter is rather 
positive. And the tweets tend to be subjective.

There's a ton of other analyses and chunking functions in 
textblob. [Read the docs](https://textblob.readthedocs.io/en/dev/quickstart.html.


> ## Challenge: Anticipating Sentiment
> Write Python code that outputs three sets of 
> sentiment values:  gasprices, catsofinsta, capitolriotsrehydrated

> When you output the three values, arrange them in what you guess
> will be the least positive to most positive sentiment.
>
> Remember, you need to pass TextBlob a string. A list will work:
> ~~~
> your_data_list = ' '.join(your_data_df['text'].tolist())
> your_data_blob = textblob.TextBlob(your_data_list)
> ~~~
> {: .source}
>
> > ## Solution
> >
> > I'm going to guess that all my datasets are going to 
> > be pretty subjective. Except for maybe ecodatascience.
> > 
> > My anticipated sentiment order:
> > - capitol
> > - gas prices
> > - library timeline
> > - ecodatascience
> > - catsofinstagram
> > - fluffl catsofinstagram
> > 
> > ~~~
> > it may also include some code
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}



## Can we do anything with the emojis?
examined Emojis as a proxy measurement of qualitative emotional 
content. ie: you can visually see sentiment in emojis.

They are emotional icons. #FIXME



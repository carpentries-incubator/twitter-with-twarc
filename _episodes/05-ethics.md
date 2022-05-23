---
title: "Ethics and Twitter"
teaching: 30
exercises: 20
questions:
- "Can I avoid seeing hate speech and unsettling imagery and still analyze twitter?"
- "What are some privacy or other ethical issues that you need to keep in mind when harvesting tweets with twarc?"
- "How much personal information can we actually gather about a user given our twarc scrape?"
- "What are some use cases that might be inappropriate?"

key points:
- "Discuss the privacy of ethical concerns surrounding tweet harvesting."
- "'Distance Reading' is analyzing big full-text data without a human consuming the words"
- "Robot detection, archives, and deleted accounts"
---


## Twitter Content

Researching tweets on Twitter may expose you to hate speech, and possibly disturbing imagery. 
Fortunately, when we work with thousands of tweets at a time, we do so at a distance,
so we can avoid consuming disturbing content directly.

First of all we need to get at the language.

## Text Analysis with Textblob

Looking at the most commonly used words and phrases in a dataset is a text analysis practice.
This helps us to get a sense of what we are dealing with in our dataset.

In Text Data Mining, a complete list of words and their frequency of appearance
is is called a 
"concordance." We would consider texts of the tweets themseves to be the corpus. 
Everything else is metadata.

We will use the TextBlob package for our full-text analysis.

~~~
hashtag_cats_df.columns
~~~
{: .language-python}

~~~
# we' see that the tweet is found under the column "text"
library_df['text'].head()
~~~
{: .language-python}

First we pull the values from the `text` column into a python list.

~~~
list_tweets = library_df['text'].tolist()
~~~
{: .language-python}

Next, we will use the python `join` function to make this list into a string of text.

~~~
string_tweets = ' '.join(list_tweets)
~~~
{: .language-python}

TextBlob has its own data format, so we need an object of that type. The function `TextBlob` 
converts the string of tweets to a textblob.

~~~
library_blob = TextBlob(string_tweets)
~~~
{: .language-python}

Now that we have our TextBlob, we can count and sort it. We do this using the python function 
`word_counts` and `sorted`.

~~~
library_freq = library_blob.word_counts
library_sorted_freq = sorted(library_freq.items(),
	key = lambda kv: kv[1], reverse = True)
print(library_sorted_freq)
~~~
{: .language-python}

This shows a lot of text with no meaning though. To help with this, we can get rid of
English stop words, like all the a's, and's, and the's.

~~~
# load the stopwords to use:
from nltk.corpus import stopwords

# sw_nltk is our dictionary of stopwords
sw_nltk = stopwords.words('english')
~~~
{: .language-python}


~~~
# create a new object without the stopwords
library_blob_stopped = textblob.TextBlob(library_words_stopped)
library_blob_stopped_freq = library_blob_stopped.word_counts
library_blob_stopped_sorted_freq = sorted(library_blob_stopped_freq.items(),
                             key = lambda kv: kv[1],
                             reverse = True)
library_blob_stopped_sorted_freq[1:50]
~~~
{: .language-python}

Lastly, we want to cut off the most used, which are http, ucsb, etc.
~~~
~~~
{: .language-python}

Can we pass this through another built-in filter?
Or pass a paramter to get only words longer than
2 characters?
We need TextBlob help #FIXME


## Just the Text
If you don't mind the obscene text, but want to avoid graphic imagery,
then there is a twarc1's utility to output an html page, and
to view the tweets in the context of a Twitter wall. This will allow
a scan of the language without showing any images:

~~~
!python utils/wall.py 'output_data/hashtagcats_flat.jsonl' > 'output_data/hashtagcats.html'
~~~
{: .language-bash}

Twitter already protects us by removing content that violates its Terms of
Use or that it otherwise finds objectionable. Sometimes this means removing
entire accounts, such as that of the former US President.

Speaking of which, let's see if data from January 6th, 2021
is still available.

> ## Challenge: January 6 Insurrectionists
>
> After the US Capitol riot, a user on kaggle captured 80,000
> Tweets from people associated with that day's events, concentrating
> on accounts from those protesting / rioting.
>
> This kaggle user, in the public interest, stored the full content of
> these Tweets as a .csv. The best practice would be to save only a
> dehydrated set of tweets. However, in this instance, we can use this
> person's conscientious objection to social norms and Twitter's
> Terms-of-Service to ask whether or not any of this is in the
> public good or an acceptable topic of research.
>
> Using the file [dehydrated_Capitol_Rioters.txt](../data/dehydratedCapitolRiotTweets.txt), determine how many
> Tweets were in the archive, and how many remain on Mr. Musk's new
> acquisition.
> {: .source}
>
> > ## Solution
> > On first run through, only 10 of the first 999 tweets remain.
> > This indicates that a huge proportion of this dataset has
> > been deleted or restricted by Twitter.
> > {: .output}
> {: .solution}
{: .challenge}

## Let's Get Ethical

There are multiple ethical issues to consider when using Twitter
data. In this lesson, we will be focusing on two issues: consent
and core legal practices.

## Authorship, the GDPR, and the Right to be Forgotten

Twitter users maintain ownership of their
tweets. As the author, users have both copyrights and
moral rights.

Copyrights prevent your tweets from being compiled together into a
publication for monetary profit. That said, some authors do not
have any copyrights. For example, POTUS is an American government employee,
therefore the property is in the Public Domain.

Laws vary greatly by country, so don't get American librarians started on
the Queen's copyrights over Canadian government data. (FIXME: expand on this)

Moral rights are more complicated. Laws vary greatly by country--even moreso than
copyright. In the European Union, authorship includes the right to un-publish,
in other words, the right to be forgotten. Twitter, very cleverly, preserves this
right by letting us delete our tweets.

GDPR defines Personal data as:

> ...Personal data are any information which are related to an identified or identifiable natural person.
>
> The data subjects are identifiable if they can be directly or indirectly identified, especially by reference to an identifier such as a name, an
> identification number, location data, an online identifier or one of several special characteristics, which expresses the physical, physiological,
> genetic, mental, commercial, cultural or social identity of these natural persons...

> ## Discussion: Personal Data
>
> Do you think that Twitter data should be treated as personal data?
> What did you consider when making this judgment?
> Are robots people?
> Do the blue checkmark people deserve privacy?
> > ## Solution
> > We get a lot of personal information when we gather tweets.
> > We can determine often determine a users’ approximate location, what they like, their beliefs, etc.
> >
{: .discussion}

## Personally identifiable information
The first two minutes of this standup comedy routine
shows the hazards of sharing too much personal information on social
media:
https://www.youtube.com/watch?v=1qqo6z_aBzU

We get a lot of personal information when we gather tweets. Enough to create
personalized ads, right?

We can determine often determine a users’ approximate location, what
they like, their beliefs, etc.

# Misinformation
Nature disinformation cloud https://media.nature.com/lw800/magazine-assets/d41586-021-00257-y/d41586-021-00257-y_18832182.png

Something about social media as a tool for people with certain motives. I wonder if theres a Parler Dataset on Kaggle? Or do you think that might violate the Carpentries code of conduct (too risky?)?

# DocTheNow’s personas

# Social Humans and robots
We can apply DocTheNow’s SH-A labels to individual Tweets to identify bots,
trolls, and malicious actors.

https://www.docnow.io/social-humans/

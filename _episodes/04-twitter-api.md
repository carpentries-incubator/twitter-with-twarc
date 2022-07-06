---
title: "The Twitter Public API"
teaching: 40
exercises: 15
questions:
- "How exactly are we using the Twitter API?"
- "What endpoints are available to me?"
- "What are the limitations of our accounts?"
- "How can I standardize my workflow?"
objectives:
- "Defining API, and what makes the Twitter API special"
- "Demonstrating other features of twarc in the context of endpoints"
keypoints:
- "There are many online sources of Twitter data"
- "Utilities and plugins come with twarc to help us out"
- "A consistant 'harvest > convert > examine' pipeline will help us work with our data"
---

## The Twitter v.2 API

The Twitter API is what allows us to collect tweets. Twarc takes care of the interactions
between our Jupyter notebook and the API. Twitter also keeps track of
who is getting this data. That's why there is that lengthy application
process tied to their
API access.

One of the ways to utilize the API access is to collect tweets and request only the information we need.

Recall that API is an acronym for Application Programming Interface. APIs allow the development of bots that generate tweets. Some examples include seismographs, weather forecasts, or delivering content on behalf of a commercial brand. Those same API features allow us to do our research.

Compared to
v1, the most recent version of the Twitter API (v2) includes additional levels of
access, more features, and faster onboarding for developers and academic
researchers. It also forced twarc to update its code, so that's why we are now
using twarc2.

The Twitter API comes along with all sorts of rules and regulations: how to
submit requests, how many requests you can make in an hour, how many Tweets you
can download in a month.

That last policy is something we should highlight. The level of API access
you have is limited to 500,000 Tweets per month. For that reason, while we
collect Tweets during this workshop, let's get in the habit of limiting ourselves
to 500 Tweets. This is a ballpark so don't be surprised if there are more or less.

~~~
!twarc2 timeline --limit 500 UCSBLibrary > 'raw/ucsblib_timeline.jsonl'
~~~
{: .language-python}

~~~
Set --limit of 500 reached:  15%|█▋         | 500/3271 [00:04<00:24, 113.41it/s]
~~~
{: .output}

So the above gives us, at most, 500 tweets from the UCSBLibrary Twitter
account's timeline. And twarc tells us that it only gave us 15% of what is available.

You can always check to see how much of your quota you have used by visiting your
[Twitter developer dashboard](https://developer.twitter.com/en/portal/dashboard). "Academic access", which is an elevated tier from "Essential Access", comes with 3 projects and 10 million tweets per month.

> ## twarc and twarc2
> With Twitter's release of the API v2, twarc2 was built to accommodate the new API.
> When we installed twarc2, the first release of twarc
> (which can be thought of as "twarc1"),
> is also installed.
> This means, you have access to some of ["twarc1" tools](https://ucsb-collaboratory.github.io/twarc/)
> when you install twarc2.
{: .callout}

## Endpoints

The Twitter API (similarly to other API's) make requests for data and deliver
data to you by calling an endpoint. An endpoint is a unique address that
corresponds to specific types of information, and marks the limit (or endpoint)
that an API may retrieve data from Twitter. The Twitter API include a range of
endpoints, and they are categorized as:

* Accounts and users
* Tweets and replies
* Direct Messages
* Publisher tools and Software Development Kits

For this lesson, we will be covering some of your endpoint options that are
available for to you as a user of the public Twitter v.2 API.  All these
endpoints apply to the Tweets and Replies that satisfy a set of parameters you
have set (e.g. Tweets from a certain account, Tweets containing a certain
hashtag, etc). These endpoints indicate *how* we may retrieve Twitter data.
twarc2 give us easy access to these endpoints as commands.

| Endpoint            | Description |
|---------------------|-------------|
| Recent Tweet counts | Retrieve the count of Tweets posted in the last 7 days. |
| Recent Search       | Access to public Tweets posted in the last 7 days. |
| Filtered Stream     | Collect Tweets as they are posted in real-time. |

When you are doing exploratory searching, these are the order you want to do
things in so that you don't waste your quota.

Filtering collects tweets as they happen in realtime. We will do a filtered
search later on. It's important to estimate how many tweets you
might get via a filtered stream before you start, so that you know
how long to run it.

### Twarc's Data

The data that is saved using twarc is just what Twitter reads from a tweet as
data and provides as data. So, keeping the data authentic for analysis is a
design of twarc. twarc is also traceable, so people can see a log of how and when
the data was collected.

In the v2 redesign, twarc was also designed to be easily part of a pipeline of
commands. Users can connect their data collecting to other pieces of their
software that expect to get tweets as inputs. When you install twarc, you will
get two clients, twarc & twarc2. Twarc was designed with the v1 Twitter API in
mind, and twarc2 was designed as a response to Twitter implementing their v2 API.

### Tweet counts endpoint
After we specify parameters for what tweets we are interested in, we are able to get a count of tweets. This allows us to gain insight on the amount of available data without needing to pull tweets and spend our limited quota.

~~~
!twarc2 counts --text "UCSB"
~~~
{: .language-bash}

The output shows there were 1,997 mentions
of UCSB on Twitter in the 7 days before the command was run.

~~~
2022-05-15T18:00:00.000Z - 2022-05-15T19:00:00.000Z: 16
2022-05-15T19:00:00.000Z - 2022-05-15T20:00:00.000Z: 17
2022-05-15T20:00:00.000Z - 2022-05-15T21:00:00.000Z: 19
...
2022-05-15T18:00:00.000Z - 2022-05-16T19:00:00.000Z: 23
2022-05-15T19:00:00.000Z - 2022-05-16T20:00:00.000Z: 22
2022-05-15T20:00:00.000Z - 2022-05-16T21:00:00.000Z: 16

Total Tweets: 1,997
~~~
{: output}

Twitter is NOT case sensitive, so these counts include various capitalizations of the key word, such as "ucsb",  "Ucsb", "UcSb", etc.

> ## Challenge: Counting Hashtags
>
> Run the following commands:
> ~~~
> !twarc2 counts --text "basketball"
> ~~~
> {: .language-bash}
>
> ~~~
> !twarc2 counts --text "(basketball #basketball)"
> ~~~
> {: .language-bash}
>
> What do you notice regarding the total tweets you receive?
> Do the same for baseball to confirm, using the terms "baseball" and "#baseball".
>
> Will a search for a word also return that word used as a hashtag?
> Does the Twitter API use a boolean `AND` or a boolean `OR` by default?
> 
> > ## Solution
> > The output of the command `twarc2 counts --text "basketball"`:
> > ~~~
> > 2022-05-18T21:23:38.000Z - 2022-05-18T22:00:00.000Z: 1,432
> > 2022-05-18T22:00:00.000Z - 2022-05-18T23:00:00.000Z: 2,507
> > ...
> > 2022-05-25T19:00:00.000Z - 2022-05-25T20:00:00.000Z: 625
> > 2022-05-25T21:00:00.000Z - 2022-05-25T21:23:38.000Z: 905
> >
> > Total Tweets: 437,140
> > ~~~
> > {: .output}
> >
> > When we do a search of some text,
> > the count will include tweets which contain the hashtag of the text.
> > In this example, the resulting count for "poker" included tweets which contain "#poker".
> >
> > The output of the command `twarc2 counts --text "(basketball #basketball)"`:
> > ~~~
> > 2022-05-18T21:25:08.000Z - 2022-05-18T22:00:00.000Z: 69
> > 2022-05-18T22:00:00.000Z - 2022-05-18T23:00:00.000Z: 67
> > ...
> > 2022-05-25T20:00:00.000Z - 2022-05-25T21:00:00.000Z: 110
> > 2022-05-25T21:00:00.000Z - 2022-05-25T21:25:08.000Z: 60
> >
> > Total Tweets: 17,308
> > ~~~
> > {: .output}
> >
> > Searching for the word "basketball" also returns uses of "#basketball". Both are included in the
> > 437,140 from the first count command (a Boolean `OR`).
> >
> > This command did a count on tweets that contained the text "basketball" and "#basketball".
> > The resulting number of 17,308 is smaller than the count from the first count command, that tells
> > us the Twitter uses a boolean AND by default. 
> >
> {: .solution}
{: .challenge}

> ## Challenge: Counting Hashtags Again
> Challenge Try using the counts command on other topics by comparing the counts from the words
> "poker" and "football". Aggregate the counts together by day. Do you think we can use these results to
> get insight on what sports are most popular on Twitter?
>
> > ## Solution
> > The `--granularity` flag for the counts command sets the time interval for aggregate counts.
> > ~~~
> > !twarc2 counts --granularity "day" --text "poker"
> > !twarc2 counts --granularity "day" --text "football"
> > ~~~
> > {: .language-bash}
> >
> > And their respective outputs:
> >
> > ~~~
> > Total Tweets: 112,077
> > Total Tweets: 1,921,740
> > ~~~
> > {: .output}
> >
> >
> {: .solution}
{: .challenge}



## Gathering Big Data

Getting a sense of the scale of the conversation on Twitter is important.
When you are starting out, you won't have much idea about how many tweets a
search will return. With a monthly limit of 500,000 tweets, it's good to use
the Recent Tweet Counts endpoint to do some exploratory searching.

You are able to get thousands of tweets when specifying your parameters to cat-related Twitter content. That’s a healthy amount of data to analyze, and cats-related content is the most popular posting on Twitter. We also looked at and compared the number of tweets related to sports content in Twitter. Sports is second in popularity, perhaps second only to political-related content.

But just how big is Twitter? Try running these counts:


> ## Type along the following commands:
> Let's try getting tweet counts for each of these common English words:
> ~~~
> !twarc2 counts --granularity "day" --text "dog"
> !twarc2 counts --granularity "day" --text "cat"
> !twarc2 counts --granularity "day" --text "amazon"
> !twarc2 counts --granularity "day" --text "right"
> !twarc2 counts --granularity "day" --text "good"
> ~~~
> {: .language-bash}
>
> > ## Solution
> >
> > ~~~
> > Their respective outputs are:
> > Total Tweets: 1,605,699  
> > Total Tweets: 2,481,676   
> > Total Tweets: 6,538,724  
> > Total Tweets: 13,321,791  
> > Total Tweets: 28,238,126  
> > ~~~
> > {: .output}
> >
> > Specific topics, such as "dog" and "cat", return lower counts compared to searches of
> > commonly used words, "right" and "good". Notice that the word "amazon" has a count that
> > is between specific topics and commonly used words. "amazon" may refer to the geographical Amazonia,
> > or the company.
> >
> > This shows the range of numbers we are able to get from Twitter, and that the
> > counts depend on the scope of the word.
> > It looks like any English word that is used on Twitter more than 10 million
> > times a week on Twitter is a fairly non-specific search.
> {: .solution}
{: .challenge}

That should give us a pretty good idea that for research use, 500,000 tweets
is plenty to handle. And again: if you need more, there is a elevated level of
access for more high-powered academics.


## Pipeline: jsonl > head & tail > wc > csv > dataframe
Just like we should keep track of how many tweets we download at any given time,
we should implement a standard workflow when gathering tweets. Generally for the
rest of this workshop, we will follow this workflow:

1. Collect Tweets as .jsonl files
2. Flatten the raw data. This is necessary when you certain commands to collect data (`timeline`, etc.)
3. Convert the flattened .jsonl file to csv
4. Use `wc` to make you received as much as you expected
5. Use `head` and `tail` to make sure you got the timespan you were expecting
6. Create a Pandas dataframe

We've already discussed that While JSON is common, it's not super
human-readable, and it can be difficult to convert to a dataframe (which most
of us will want to do anyway). So twarc2 has an extension to turn our harvested
jsonl to csv. csv's are always easily convertible into Pandas dataframes.

So let's flatten the UCSBLibrary timeline and convert the flattened data to a csv:

~~~
!twarc2 flatten raw/ucsblib_timeline.jsonl output/ucsblib_timeline_flat.jsonl
!twarc2 csv output/ucsblib_timeline_flat.jsonl output_data/ucsblib_timeline.csv
~~~
{: .language-bash}

~~~
100%|████████████████| Processed 282k/282k of input file [00:00<00:00, 27.6MB/s]
100%|████████████████| Processed 539k/539k of input file [00:00<00:00, 5.50MB/s]

ℹ️
Parsed 500 tweets objects from 500 lines in the input file.
Wrote 500 rows and output 74 columns in the CSV.
~~~
{: .output}

Now that we have the csv of the data, we can use a python pandas command to get the data into a dataframe.

~~~
ucsblib_timeline_df = pd.read_csv("output/ucsblib_timeline.csv")

#outputs first 5 lines in dataframe
ucsblib_timeline_df.head()
~~~
{: .language-python}

~~~
#outputs last 5 lines in dataframe
ucsblib_timeline_df.tail()
~~~
{: .language-python}

Use `wc` to get a count of tweets. Did we get a reasonable amount?

Let's remind ourselves of some of the different things that come
along with a tweet by printing out a list of the dataframe
headers:

~~~
#outputs first 5 columns
ucsblib_timeline_df.columns[:5]
~~~
{: .language-python}

~~~
Index(['id', 'conversation_id', 'referenced_tweets.replied_to.id',
       'referenced_tweets.retweeted.id', 'referenced_tweets.quoted.id'],
      dtype='object')
~~~
{: .output}

We can see some of the column headers here. Looking through these column headers, we can see what data information we may look into.
For example:

The column 'public_metrics.retweet_count' provides a total count of retweets for each tweet.

~~~
#grab only specified column
ucsblib_timeline_df['public_metrics.retweet_count']
~~~
{: .language-python}

By using the Python function `.sort_values()`, we can sort the dataframe 
in order of Retweet counts. That's a measure of how much impact that tweet
had online.

~~~
sort_by_rt = ucsblib_timeline_df.sort_values('public_metrics.retweet_count', ascending=False)

#the first tweet from the sorted dataframe
most_rt = sort_by_rt.head(1)

#output only the text of the tweet
most_rt['text']
~~~
{: .language-python}

You may also get the tweet id to view the tweet on Twitter:
https://twitter.com/UCSBLibrary/status/tweet_id


Another metric is how many times a tweet has been 'retweeted with quote',
by looking at the column "public_metrics.quote_count":

~~~
sort_by_qc = ucsblib_timeline_df.sort_values("public_metrics.quote_count", ascending=False)

#the first tweet from the sorted dataframe
most_quoted = sort_by_qc.head(1)

#output only the text of the tweet
most_quoted['text']
~~~
{: .language-python}

It takes a bit more effort to retweet-with-quote rather than just pushing the
Retweet button, so these can be considered more impactful.

Finally, you can see who the most impactful author is in your dataset by 
looking at "author.public_metrics.followers_count". For timelines, this will look at both @UCSBlibrary and any accounts @UCSBlibrary retweeted from in the timeline we collected.

~~~
sort_by_fol = ucsblib_timeline_df.sort_values('author.public_metrics.followers_count', ascending=False)

#the first tweet from the sorted dataframe
most_fol = sort_by_fol.head(1)

#output only the id of the tweet
most_fol['id']
~~~
{: .language-python}

> ## Challenge: Hashtag Cats of Instagram
> Let's get a reasonably sized dataset to use for the remainder of
> the workshop. Harvest 500 tweets that use the hashtag "catsofinstagram"
> and put the dataset through our pipeline (harvest > flatten > csv > 
> dataframe) to answer the following questions:
>
> 1. Did you get exactly 500 tweets?
> 2. How far back in time did you get?
> 3. What is the most re-tweeted tweet from our search?
> 4. Which person has the most number of followers in your dataset?
>
> > ## Solution
> > ~~~
> > !twarc2 search --limit 500 "#catsofinstagram" raw/catsofinstagram.jsonl
> > ~~~
> > {: .language-bash}
> >
> > 1. Let's start by converting our dataset to a csv, then run some python
> > ~~~
> > !twarc2 csv raw/catsofinstagram.jsonl output/catsofinstagram.csv
> > ~~~
> > {: .language-bash}
> >
> > Read in csv using pandas. Pandas is denoted by pd.
> > ~~~
> > cats_df = pd.read_csv("output/catsofinstagram.csv")
> > ~~~
> > {: .language-python}
> >
> > We are able to see how many tweets we get by getting the dimensions of the dataframe
> > or with `wc`.
> > The number of rows indicate the number of unique tweets. The dumber of columns indicate
> > the amount of data that came with each tweet.
> > ~~~
> > cats_df.shape
> > ~~~
> > {: .language-python}
> >  
> >
> > 2. Look at the earliest value under the column 'created_at'.
> > Technically, you don't have to sort this, since tweets arrive chronologically.
> > ~~~
> > earliest_create = cats_df.sort_values('created_at', ascending = True).head(1)
> > earliest_create['created_at']
> > ~~~
> > {: .language-python}
> >
> > 3.
> > ~~~
> > most_rt = cats_df.sort_values('public_metrics.retweet_count', ascending = False).head(1)
> >
> > most_rt['text']
> > ~~~
> > {: .language-python}
> >
> > 4.
> > ~~~
> > most_fol = cats_df.sort_values('author.public_metrics.followers_count', ascending = False).head(1)
> > most_fol['id']
> > ~~~
> > {: .language-python}
> >
> > User with author_id 248757990 has the most followers, which is 2086382.
> >
> > We can then get the information on the user.
> > ~~~
> > !twarc2 user id 248757990
> > ~~~
> > {: .language-bash}
> >
> >
> {: .solution}
{: .challenge}

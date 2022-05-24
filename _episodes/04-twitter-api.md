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

The Twitter API is what allows us to collect tweets. Twitter also keeps track of who is getting this data, and which is why there is an application tied to their API access.

One of the ways to utilize the API access is to collect tweets and request only the information we need.

Recall that API is an acronym for Application Programming Interface. APIs allow the development of bots that generate tweets. Some examples include seismographs, weather forecasts, or delivering content on behalf of a commercial brand. Those same API features allow us to do our research.

Compared to
v1, the most recent version of the Twitter API (v2) includes additional levels of
access, more features, and faster onboarding for developers and academic
researchers.

The Twitter API comes along with all sorts of rules and regulations: how to
submit requests, how many requests you can make in an hour, how many Tweets you
can download in a month.

That last policy is something we should highlight. The level of API access
you have is limited to 500,000 Tweets per month. For that reason, while we
collect Tweets during this workshop, let's get in the habit of limiting ourselves
to 500 Tweets. This is a ballpark so don't be surprised if there are more or less.

~~~
!twarc2 timeline --limit 500 UCSBLibrary > 'raw_data/ucsblib_timeline.jsonl'
~~~
{: .language-python}

~~~
Set --limit of 500 reached:  15%|█▋         | 500/3271 [00:04<00:24, 113.41it/s]
~~~
{: .output}

So the above gives us, at most, 500 tweets from the UCSBLibrary Twitter
account's timeline. And twarc tells us that it only gave us 15% of what is available.

You can always check to see how much of your quota you have used by visiting your
[Twitter developer dashboard](https://developer.twitter.com/en/portal/dashboard)

> ## Academic access
> Academic access comes with 3 projects and 10 million tweets per month.
>
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
Twarc2 give us easy access to these endpoints as commands.

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

The data that is saved using Twarc is just what Twitter reads from a tweet as
data and provides as data. So, keeping the data authentic for analysis is a
design of Twarc. Twarc is also traceable, so people can see a log of how and when
the data was collected.

In the v2 redesign, Twarc was also designed to be easily part of a pipeline of
commands. Users can connect their data collecting to other pieces of their
software that expect to get tweets as inputs. When you install Twarc, you will
get two clients, twarc & twarc2. Twarc was designed with the v1 Twitter API in
mind, and Twarc2 was designed as a response to Twitter implementing their v2 API.

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

> ## Challenge: Sports on Twitter
> Challenge Try using the counts command on other topics by comparing the counts from the words "poker", "golf",
> "basketball", "baseball", and "football". Aggregate the counts together by day. Can we use these results to
> imagine what sports are most popular on Sports Twitter? Discuss.
>
> > ## Solution
> > The `--granularity` flag for the counts command sets the time interval for aggregate counts.
> > ~~~
> > !twarc2 counts --granularity "day" --text "(Poker OR poker OR #Poker OR #poker)"
> > !twarc2 counts --granularity "day" --text "(Golf OR golf OR #Golf OR #golf)"
> > !twarc2 counts --granularity "day" --text "(Basketball OR basketball OR #Basketball OR #basketball)"
> > !twarc2 counts --granularity "day" --text "(Baseball OR baseball OR #Baseball OR #baseball)"
> > !twarc2 counts --granularity "day" --text "(Football OR football OR #Football OR #football)"
> > ~~~
> > {: .language-bash}
> >
> > And their respective outputs:
> >
> > ~~~
> > Total Tweets: 108,021  
> > Total Tweets: 344,462  
> > Total Tweets: 471,942  
> > Total Tweets: 720,510  
> > Total Tweets: 1,789,262  
> > ~~~
> > {: .output}
> >
> > From our output, football appears to be the most popular sport on Twitter currently, followed by baseball.
> >
> {: .solution}
{: .challenge}

## Recent Search

This endpoint gathers the most recent 6 days of a search string that
you pass to the API via twarc. Let's gather all the recent mentions of
the UCSB Library.

Both filter and search use
<a href="https://twitter.com/search-advanced?lang=en" target="new">Twitter's advanced search syntax</a>
We can use a little Boolean logic to make sure we cast
a wide net, ie: that we search a variety of text strings and hashtags.

~~~
!twarc2 counts --granularity "day"
        --text "(#UCSBLibrary OR UCSBLibrary OR
                 ucsblibrary OR #ucsblibrary OR
                 davidsonlibrary OR #davidsonlibrary)"
~~~
{: .language-bash}

The `OR` is necessary for syntax. Twitter is NOT case sensitive, so we want to specify the counts command to include various capitalizations.

~~~
!twarc2 counts --granularity "day" --text "(#UCSBLibrary OR UCSBLibrary)"`
~~~
{: .language-bash}

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

Timelines need to run through the `flatten` twarc plug-in.
We still haven't found another datatype that needs to be flattened. #FIXME ?

So let's flatten the UCSBLibrary timeline, count up our tweets,
convert to CSV, and create a dataframe

~~~
!twarc2 flatten raw_data/ucsblib_timeline.jsonl output_data/ucsblib_timeline_flat.jsonl
!twarc2 csv output_data/ucsblib_timeline_flat.jsonl output_data/ucsblib_timeline.csv
~~~
{: .language-bash}

~~~
ucsblib_timeline_df = pandas.read_csv("output_data/ucsblib_timeline.csv")
ucsblib_timeline_df.head()
ucsblib_timeline_df.tail()
~~~
{: .language-python}

Use `wc`: Did we get a reasonable amount?

Let's remind ourselves of all the different things that come
along with a tweet by printing out a list of the dataframe
headers:

~~~
ucsblib_timeline_df.columns
~~~
{: .language-python}

<<<<<<< HEAD
and see the column headers here as a list.

#FIXME write the code for below:
Easy 'analyses' using our dataframe:
Call each of these elements out of the dataframe by sorting:
- most retweeted
- most quoted
- tweeter with the most number of followers


~~~
Index(['id', 'conversation_id', 'referenced_tweets.replied_to.id',
       'referenced_tweets.retweeted.id', 'referenced_tweets.quoted.id',
       'author_id', 'in_reply_to_user_id', 'retweeted_user_id',
...
       '__twarc.retrieved_at', '__twarc.url',
       '__twarc.version', 'Unnamed: 73'],
      dtype='object')
~~~
{: .output}

We can see the column headers here.


> ## Challenge: Cats of Instagram
> Let's make a bigger datafile. Harvest 500 tweets that use the hashtag "catsofinstagram"
> and put the dataset through the pipeline to answer the following questions:
>
> 1. Did you get exactly 500?
> 2. How far back in time did you get?
> 3. What is the most re-tweeted recent tweet on #catsofinstagram?
> 4. Which person has the most number of followers in your dataset?
>
> > ## Solution
> > ~~~
> > !twarc2 search --limit 500 "#catsofinstagram" source-data/catsofinstagram.jsonl
> > ~~~
> > {: .language-bash}
> >
> > 1. Let's start by converting our dataset to a csv, then run some python
> > ~~~
> > !twarc2 csv source-data/catsofinstagram.jsonl output-data/catsofinstagram.csv
> > ~~~
> > {: .language-bash}
> >
> > Read in csv using pandas. Pandas is denoted by pd.
> > ~~~
> > cats_df = pd.read_csv("output-data/catsofinstagram.csv")
> > ~~~
> > {: .language-bash}
> >
> > We are able to see how many tweets we get by getting the dimensions of the dataframe.
> > The number of rows indicate the number of unique tweets. The dumber of columns indicate
> > the amount of data that came with each tweet.
> > ~~~
> > cats_df.shape
> > ~~~
> > {: .language-bash}
> >  
> >
> > 2.
> >
> > Print the earliest value under the column 'created_at'.
> > ~~~
> > cats_df[cats_df.created_at == cats_df.created_at.min()].loc[:,'created_at']
> > ~~~
> > {: .language-bash}
> >
> > The earliest time from our dataset is 05/17/2022 at 144:50:26 pm.
> >
> > 3. We can do this by finding the max number of retweets in the dataset and then.
> > ~~~
> > most_rt = cats_df[cats_df['public_metrics.retweet_count'] ==
> > cats_df['public_metrics.retweet_count'].max()].head()
> >
> > print(most_rt.text)
> > ~~~
> > {: .language-python}
> >
> > ~~~
> > '❃❃❃ PURE LOVE ❤💘❤\n#CatsOfTwitter #catsofinstagram #cats https://t.co/kIbFkKFWeT'.
> > ~~~
> > {: .output}
> >
> > 4. We can calculate the max number of follows in the dataset and then select the tweet that meets that requirement.
> > ~~~
> > most_fo = cats_df[cats_df['author.public_metrics.followers_count'] == cats_df['author.public_metrics.followers_count'].max()].head()
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

---
title: "The Twitter Public API"
teaching: 0
exercises: 0
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

If we are to retreive data, Twitter does not give us a huge data load of csv's or 
other giant files of data (we would not want that anyways). Instead Twitter makes 
data access available to researchers that apply for the twitter api. The Twitter 
Api allows applicants to collect tweets. This is also so Twitter can keep track 
of who is getting this data, and monitor data use.

Recall that API is an acronym for Application Programming Interface. Compared to 
v1, the most recent version of the Twitter API (v2) includes additional levels of 
access, more features, and faster onboarding for developers and academic 
researchers.

The Twitter API comes along with all sorts of rules and regulations: how to 
submit requests, how many requests you can make in an hour, how many Tweets you 
can download in a month.

That last regulation is something we should highlight. The level of API access 
you have is limited to 500,000 Tweets per month. For that reason, while we 
collect Tweets during this workshop, let's get in the habit of limiting ourselves 
to 500 Tweets.

~~~
!twarc2 timeline --limit 500 UCSBLibrary > 'source-data/ucsblib.jsonl'
~~~
{. :language-python}

~~~
Set --limit of 500 reached:  15%|█▋         | 500/3271 [00:04<00:24, 113.41it/s]
~~~
{: .output}

So the above gives us, at most, 500 tweets from the UCSBLibrary Twitter 
account's feed.

You can always check to see how much of your quota you have used by visiting your 
[Twitter developer dashboard](https://developer.twitter.com/en/portal/dashboard)

> ## Academic access
> Academic access comes with 3 projects and 10 million tweets per month.
>
{: .callout}

## Twarc let’s you interact via the v1 api and v2 api.
We already did twarc2 timeline. Twarc1 timeline gives slightly different results 
(We need to confirm and figure out how they are different?). How are they 
different?

Remember: timeline captures tweets of 1 person: this harvests up to some 
arbitrary limit below 3200 You can request a specific time period for a person’s 
timeline: Dong dong dong

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


## Twarc's Data Collection

The data that is saved using Twarc is just what Twitter reads from a tweet as 
data and provides as data. So, keeping the data authentic for analysis is a 
design of Twarc. Twarc is also traceable, so people can see a log of how and when 
the data was collected.

In the v2 redesign, Twarc was also designed to be easily part of a pipeline of 
commands. Users can connect their data collecting to other pieces of their 
software that expect to get tweets as inputs. When you install Twarc, you will 
get two clients, twarc & twarc2. Twarc was designed with the v1 Twitter API in 
mind, and Twarc2 was designed as a response to Twitter implementing their v2 API.

## Tweet counts
Allows you to fish around to estimate traffic without spending your quota

~~~
!twarc2 counts --text "kittens"
~~~
{: .bash}

Output: screenshot of the bottom of the output showing there were 95,767 mentions 
of kittens on twitter in the 7 days before the command was run. #FIXME

# Challenge

Format this as a challenge: #FIXME

Try counting 
mentions of the words poker, golf, basketball, baseball, and football. Aggregate
then counts together by day. Can we use these results to imagine what sports are
most popular on Sports Twitter? Discuss.


## Filtered Stream
Filtering collects tweets as they happen in realtime. We will do a filtered
search later on. It's important to estimate how many tweets you
might get via a filtered stream before you start, so that you know
how long to run it.

## Recent Search
This endpoint gathers the most recent 6 days of a search string that
you pass to the API via twarc. Let's gather all the recent mentions of 
the UCSB Library. 

Both filter and search use (Twitter's advanced search
syntax)[https://twitter.com/search-advanced?lang=en]. 
We can use a little Boolean logic to make sure we cast 
a wide net, ie: that we search a variety of text strings and hashtags.

`!twarc2 counts --granularity "day" 
        --text "(#UCSBLibrary OR UCSBLibrary OR 
                 ucsblibrary OR #ucsblibrary OR 
                 davidsonlibrary OR #davidsonlibrary)"`

Is it worth doing the OR's? For sure. Twitter is case sensitive, and we really
are string searching, so the hashtag counts.

`!twarc2 counts --granularity "day" --text "(#UCSBLibrary OR UCSBLibrary)"`

## Big Data
### What's a lot?
Getting a sense of the scale of the conversation on Twitter is important. 
When you are starting out, you won't have much idea about how many tweets a 
search will return. With a monthly limit of 500,000 tweets, it's good to use
the Recent Tweet Counts endpoint to do some exploratory searching.

We got almost 100,000 kitten tweets. That's a healthy amount of data to analyze. We
also compared the numbers on Sports Twitter--second in size perhaps only to 
Politics Twitter. 

But just how big is Twitter? Try running these counts:

## What's a lot?
Let's try getting tweet counts for each of these common English words:
- !twarc2 counts --text "dog" --granularity "day"
- !twarc2 counts --text "cat" --granularity "day"
- !twarc2 counts --text "amazon" --granularity "day"
- !twarc2 counts --text "right" --granularity "day"
- !twarc2 counts --text "good" --granularity "day"

It looks like any English word that is used on Twitter more than 10 million
times a week on Twitter is a fairly non-specific search.

That should give us a pretty good idea that for research use, 500,000 tweets
is plenty to handle. And again: if you need more, there is a elevated level of
access for more high-powered academics.


## Pipeline: jsonl > head & tail > wc > csv > dataframe 
Just like we should keep track of how many tweets we download at any given time,
we should implement a standard workflow when gathering tweets. Generally for the
rest of this workshop, we will follow this workflow:

-1 harvest json
-1 flatten if necessary (when using timeline, etc.)
-1 convert to csv
-1 use wc to make you received as much as you expected
-1 use twarc utilities and twarc2 plug-ins
-1 create a Pandas dataframe
-1 use external utiities for further analysis

While JSON is common, it's not super human-readable, and it can be difficult to 
convert to a dataframe (which most of us will want to do anyway). So twarc2 
has an extension to turn our harvested jsonl
to csv. csv's are always easily convertable into Pandas dataframes.

Timelines need to be flattened. XXX What else needs to be flattened? XXX That's
the next step in our workflow

XXX flatten the UCSBLibrary timeline XXX

Convert to CSV:
Here is where we can see the headers.

Use wc: is it a reasonable amount? 

functions that we can use.

!twarc2 csv output-data/ucsblib_timeline_flattened.jsonl output-data/ucsblib_timeline.csv

and we can load that into a pandas dataframe:

~~~
code
~~~
{: .language-python}

and see the column headers here as a list.

Easy 'analyses' using our dataframe:
- most retweeted
- most quoted
- tweeter with the most number of followers


~~~
list(kittens_df.columns)
~~~
{: .language-python}

# Final challenge: Cats of instagram

> Let's make a bigger datafile. Harvest 5000 tweets that use the hashtag "catsofinstagram"
> and put the dataset through the pipeline to answer the following questions:
> 
> 1. Did you get exactly 5000?
> 1. How far back in time did you get?
> 1. What is the most re-tweeted recent tweet on #catsofinstagram?
> 1. Which person has the most number of followers in your dataset? 
> 1. Is it really a person?
{. :challenge}


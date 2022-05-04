---
title: "The Twitter Public API"
teaching: 0
exercises: 0
questions:
- "How exactly are we using the Twitter API?"
- "What endpoints are available to me?"
- "Working within our limits"
objectives:
- "Defining API, and what makes the Twitter API special"
- "Demonstrating other features of twarc in the context of endpoints"
keypoints:
- "A simpler example: URL parameter API’s"
- "There are many online sources of Twitter data"
---

## The Twitter v.2 API

If we are to retreive data, Twitter does not give us a huge data load of csv's or other giant files of data (we would not want that anyways). Instead Twitter makes data access available to researchers that apply for the twitter api. The Twitter Api allows applicants to collect tweets. This is also so Twitter can keep track of who is getting this data, and monitor data use.

Recall that API is an acronym for Application Programming Interface. Compared to v1, the most recent version of the Twitter API (v2) includes additional levels of access, more features, and faster onboarding for developers and academic researchers.

The Twitter API comes along with all sorts of rules and regulations: how to submit requests,
how many requests you can make in an hour, how many Tweets you can download in a month.

That last regulation is something we should highlight. The level of API access you have is limited
to 500,000 Tweets per month. For that reason, while we collect Tweets during this
workshop, let's get in the habit of limiting ourselves to 500 Tweets.

~~~
!twarc2 timeline --limit 500 UCSBLibrary > 'source-data/ucsblib.jsonl'
~~~
{. :language-python}

~~~
Set --limit of 500 reached:  15%|█▋         | 500/3271 [00:04<00:24, 113.41it/s]
~~~
{. :output}

You can always check to see how much of your quota you have used by visiting your [Twitter developer dashboard](https://developer.twitter.com/en/portal/dashboard)

> ## Academic access
> Academic access comes with 3 projects and 10 million tweets per month.
>
{: .callout}

## Twarc let’s you interact via the v1 api and v2 api.
We already did twarc2 timeline. Twarc1 timeline gives slightly different results (We need to confirm and figure out how they are different?). How are they different?

Remember: timeline captures tweets of 1 person: this harvests up to some arbitrary limit below 3200
You can request a specific time period for a person’s timeline:
Dong dong dong

## Endpoints

The Twitter API (similarly to other API's) make requests for data and deliver data to you by calling an endpoint. An endpoint is a unique address that corresponds to specific types of information, and marks the limit (or endpoint) that an API may retrieve data from Twitter. The Twitter API include a range of endpoints, and they are categorized as:

* Accounts and users
* Tweets and replies
* Direct Messages
* Publisher tools and Software Development Kits

For this lesson, we will be covering some of your endpoint options that are available for to you as a user of the public Twitter v.2 API.  All these endpoints apply to the Tweets and Replies that satisfy a set of parameters you have set (e.g. Tweets from a certain account, Tweets containing a certain hashtag, etc). These endpoints indicate  *how* we may retrieve Twitter data, and you will find that Twarc makes these options available as commands.

| Endpoint            | Description |
|---------------------|-------------|
| Recent Search       | Access to public Tweets posted in the last 7 days. |
| Recent Tweet counts | Retrieve the count of Tweets posted in the last 7 days. |
| Filtered Stream     | Collect Tweets as they are posted in real-time. |

## Twarc's Data Collection

The data that is saved using Twarc is just what Twitter reads from a tweet as data and provides as data. So, keeping the data authentic for analysis is a design of Twarc. Twarc is also traceable, so people can see a log of how and when the data was collected.

In the v2 redesign, Twarc was also designed to be easily part of a pipline of commands. Users can connect their data collecting to other pieces of their software that expect to get tweets as inputs. When you install Twarc, you will get two clients, twarc & twarc2. Twarc was designed with the v1 Twitter API in mind, and Twarc2 was designed as a response to Twitter implementing their v2 API.

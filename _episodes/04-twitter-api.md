---
title: "The Twitter Public API"
teaching: 0
exercises: 0
questions:
- "How exactly are we using the Twitter API?"
- "What are some other ways of getting at Tweets?"
- "Show us more features of twarc"
objectives:
- "Defining API, and what makes the Twitter API special. Search vs Filter"
keypoints:
- "A simpler example: URL parameter API’s"
- "There are many online sources of Twitter data"
- "Twarc has .py utilities that you can upload to your notebook."

---

# The Twitter v.2 API

Recall that API is an acronym for Application Programming Interface. The Twitter API can be used to retrieve Twitter data for analysis. Compared to v1, the most recent version of the Twitter API (v2) includes additional levels of access, more features, and faster onboarding for developers and academic researchers.

The Twitter API comes along with all sorts of rules and regulations: how to submit requests,
how many requests you can make in an hour, how many Tweets you can download in a month.

That last regulation is something we should highlight. The level of API access you have is limited
to 500,000 Tweets per month. For that reason, while we collect Tweets during this
workshop, let's get in the habit of limiting ourselves to 500 Tweets.

You can always check to see how much of your quota you have used by visiting your [twitter developer dashboard](https://developer.twitter.com/en/portal/dashboard)

Remember: timeline captures tweets of 1 person: this harvests up to some arbitrary limit below 3200
You can request a specific time period for a person’s timeline:
Dong dong dong


## First look at the search command
Let's make a new cell in our Notebook and run a search command. Remember that
we need to specify an output file. `>` optional

~~~
!twarc2 search --limit 500 "#catsofinstagram" hashtag_cats.jsonl
~~~
{: .source}

![image "the output from two twarc searches"](../fig/cats.png){: .image-with-shadow}

This command will search for any recent tweets that contain #catsofinstagram. Twarc tells me that I hit my limit of 500 after checking back in after a few hours.

We can use the visual indicator to confirm the limit of our second search. We may also open the file and see if we have something less than 5000 tweets or 6 days worth.

If you want to go back as far in time as the Twitter API allows (6 days typically),
you can simultaneously tighten up your search parameters and keep your `--limit` value low.

`twarc2 search --limit 500 "catsofinstagram AND cute"`

That got me back 5 out of six days. So asking for 800 Tweets should get me all six days' worth
of results

`twarc2 search --limit 800 "catsofinstagram AND cute"`

In this way we can 'sip' at our quota and make sure we can work all month. Later on in the workshop, we will be going over to set more search parameters with this command.

> ## Academic access
> Academic access comes with 3 projects and 10 million tweets per month.
>
{: .callout}

## First look at the stream command

You may also collect tweets as they are posted, and establish rules to what tweets will be collected (as you did for setting search parameters). To start with a stream, let's set some search rules:

~~~
!twarc2 stream-rules add #catsofinstagram
~~~
{: .language-python}

~~~
!twarc2 stream-rules add #catsoftwitter
~~~
{: .language-python}

To see what your current stream rules are, you may list them:

~~~
!twarc2 stream-rules list
~~~
{: .language-python}

When you start collecting tweets with the rules you have set in place, you must create the file that the data will be stored in:

~~~
!twarc2 stream > 'source_data/streamed_tweets.jsonl'
~~~
{: .language-python}

Once this command is run, you will collect tweets that match the rules set in place. This collection will be ongoing unless you explicitly shut down the stream with `ctrl + c`. While this stops the stream collection, it does not remove the stream-rules. In order to remove the rules you had set in place, you must use delete:

~~~
!twarc2 stream-rules delete #catsofinstagram
!twarc2 stream-rules delete #catsoftwitter
~~~
{: .language-python}

> ## Discuss: Search vs Stream
> We had an introductory look at the use of the search command and the stream command.
> Please brainstorm what the difference(s) are between searching tweets and streaming tweets.
> When might you choose stream over search? How can you use them together?
{: .discussion}

## Twarc let’s you interact via the v1 api and v2 api.
We already did twarc2 timeline. Twarc1 timeline gives slightly different results (We need to confirm and figure out how they are different?). How are they different?

Functions and utilities: refer to our guide and readthedocs.docnow. There will be more detail in episode 6.
Functions / extensions: can be pip installed --and these installs stick in our Labs environment (because we
have permission to install things on top of twarc)

Our twitter guide gives advice about how to follow a real-time event, like pending #scotus decisions.

---
title: "Search and Filter"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "Search vs Filter"
keypoints:
- "Search:, Filter: (FIXME)"
---

# Search

Returns pre-existing tweets from the past 7 days that match a given query.

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

# Filter

Collects tweets as they happen. This will run as long as you let it.

Here is more [clarification](https://scholarslab.github.io/learn-twarc/06-twarc-command-basics).

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

Functions and utilities: refer to our guide and readthedocs.docnow. There will be more detail in episode 6.
Functions / extensions: can be pip installed --and these installs stick in our Labs environment (because we
have permission to install things on top of twarc)

Our twitter guide gives advice about how to follow a real-time event, like pending #scotus decisions.

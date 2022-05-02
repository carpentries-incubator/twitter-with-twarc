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

# What is an API?

API is an acronym for Application Programming Interface.


# The Twitter v.2 API

The Twitter API comes along with all sorts of rules and regulations: how to submit requests,
how many requests you can make in an hour, how many Tweets you can download in a month.

That last one is something we should highlight. The level of API access you have is limited
to 500,000 Tweets per month. For that reason, while we Search or Stream Tweets during this
workshop, let's get in the habit of limiting ourselves to 500 Tweets.

You can always check to see how much of your quota you have used by visiting your [twitter developer dashboard](https://developer.twitter.com/en/portal/dashboard)

Let's make a new cell in our Notebook and send a search:
~~~
!twarc2 search --limit 500 "#catsofinstagram" hasgtag_cats.jsonl
~~~
{: .source}

![image "the output from two twarc searches"](../fig/cats.png){: .image-with-shadow}

twarc tells me that I hit my limit of 500 after checking back in after a few hours.

We can use the visual indicator for this. Or open the file and see if we have something
less than 5000 or 6 days.

As before, let's flatten our dataset (or convert it to a csv), and figure out if we
got our full 500 Tweets. Check the first and last Tweet to determine the timespan?


If you want to go back as far in time as the Twitter API allows (6 days typically),
you can simultaneously tighten up your search parameters (using all of Twitter's
[advanced search syntax]() and keep your --limit low.

`twarc2 search --limit 500 "catsofinstagram AND cute"`

That got me back 5 out of six days. So asking for 800 Tweets should get me all six days' worth
of results

`twarc2 search --limit 800 "catsofinstagram AND cute"`

In this way we can 'sip' at our quota and make sure we can work all month.

We can also take a completely random sample of the 'firehose' to make sure that we go
back in time as far back as the Twitter API allows:

~~~
twarc2 sample

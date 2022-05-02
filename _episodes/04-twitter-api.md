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

Let's make a new cell in our Notebook and send a search:
~~~
twarc2 search --limit 500 "#catsofinstagram" hasgtag_cats.jsonl
~~~
{: .source}
~~~
can I put an image here?
![image "the output from two twarc searches"](../fig/cats.png){: .image-with-shadow}
~~~
{: .output}

 
As before, flatten your dataset, and figure out if we got our full 500 Tweets. What's the 
timespan?

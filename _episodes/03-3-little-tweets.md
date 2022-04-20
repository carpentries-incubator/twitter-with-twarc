---
title: "Anatomy of a tweet: structure of a tweet as JSON"
teaching: 0
exercises: 0
questions:
- What does twarc data look like?
- What are some ways of looking at JSON data?
- Which pieces of a tweet should I pay attention to?

objectives:
- Getting acquainted with a dataset

keypoints:
- Tweets arrive as JSON, a super common format.
- We can use any old xml viewer to look at JSON
- Tweets come with a TON of associated data
---

# Examining a twarc JSON file

JSON is a flavor of xml and is frequently used as a data interchange
format. It has become super common in the data science field, and you will 
encounter it frequently. 

Let's look at our `taxday.jsn` file again. Remember that our JSON files are line-oriented,
ie: one tweet per line. Let's use `head -n 1 taxday.jsn > 1-tweet.json` to create a file
with just our first three tweets.

{% include links.md %}

> ## Challenge Title
>
> Using the shell, output the first 2 and last 2 tweets in `taxday.jsn`.
> Download the file and view it in your web browser. 
> 1 How long is the time difference between the first and the last tweets?
> 2 Judging by these 4 tweets, do they arrive in chronological order?
> 

> ~~~
> it may include some code
> ~~~
> {: .source}
>
> > ## Solution
> >
> > 1 Answer
> > 2 Answer
> > ~~~
> > it may also include some code
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

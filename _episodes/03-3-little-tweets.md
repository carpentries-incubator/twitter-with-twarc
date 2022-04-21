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

Let's look at our `taxday.jsonl` file again. Remember that our JSON files are line-oriented,
ie: one tweet per line. Let's use `head -n 1 taxday.jsonl > 1-tweet.jsonl` to create a file
with just our first three tweets.

If we use `cat` to output that file to the screen, we see a real mess. Let's
open the file with a graphical text editor instead. 

> ## Why jump out of BASH?
>
> We should be using nano instead, but we don't have access to nano
> in our little shell window. 
> {: .source}
{: .callout}

In Sublime Text, it's still difficult to tell what's going on. But because line numbering is
turned on, we can see that this whole screen is still the first Tweet. Are these all a whole
bunch of named-value pairs? ie:

~~~
"name": "Joe Gaucho",
"address": "123 Del Playa",
"age": 23,
fav_foods: "Field tortillas",
~~~

Is that what Tweets look like? If we unwrap the text, indeed: each line of JSON is a Tweet,
and JSON is a series of comma-separated name-value pairs. 

### link to a page with a good view of tweets
This pdf is old: http://www.slaw.ca/wp-content/uploads/2011/11/map-of-a-tweet-copy.pdf


{% include links.md %}

> ## Challenge Title
>
> Using the shell, output the first 2 and last 2 tweets in `taxday.jsn`.
> Download the file and view it in your web browser. 
> 1 How long is the time difference between the first and the last tweets?
> 2 Judging by these 4 tweets, do they arrive in chronological order?
> 

> ~~~
> head -n 2 > 4tweets.jsonl
> tail -n 2 >> 4tweets.jsonl
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

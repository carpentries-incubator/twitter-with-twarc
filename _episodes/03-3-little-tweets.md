---
title: "Anatomy of a tweet: structure of a tweet as JSON"
teaching: 10
exercises: 10
questions:
- What does Twitter data look like?
- What are some ways of looking at Twitter JSONL data?
- Which pieces of a tweet should I pay attention to?

objectives:
- Getting acquainted with a dataset

keypoints:
- Tweets arrive as JSONL, a super common format.
- We can use online viewers for a human-readable look at JSONL
- Tweets come with a TON of associated data
---

# Examining a twarc JSON file

JSONL, Line-oriented JavaScript Object Notation, is frequently used as a 
data interchange format. It has become super common in the data science 
field, and you will encounter it frequently. On April 18th, 2022, we 
used twarc to search for all mentions of the hashtag `#taxday` (April 15th is
the typical deadline for Americans to file their annual income report,
but in 2022, it was April 18).

Let's look at that individual tweet again.

The Jupyter viewer has numbering, so we can see that this whole screen 
is one line. Where the content starts, it becomes obvious that JSON is a 
whole bunch of named-value pairs? ie:

~~~
"name": "Joe Gaucho",
"address": "123 Del Playa",
"age": 23,
fav_foods: "Field tortillas",
~~~

In nano, we can start to format this a bit with returns and indents. You can see that 
the key is in quotes, then there's a colon, then the value. If the value is text,
that's going to be in quotes too.

Let's crawl along until we find the tweet text itself.

We can see that the tweet itself is the 4th piece of data in the tweet,
after the author's ID, the language, and the time stamp. The fifth
element tells us that this tweet is in reply to another tweet.

There are many, many elements attached to each Tweet. You will probably never use
most of them. 

Some key pieces of a Tweet are:
- created_at
- id
- entities
  -- any hashtags that are used
  -- any users who are @'ed
- user
  -- id
  -- name
  -- screen name (twitter handle)
  -- followers_count
  
All of these elements become much more visible if we download our tweet 
and open it up with (an online JSONL viewer)[https://codebeautify.org/jsonviewer] 

* screenshot goes here *

(need to write a bit more about the first tweet)

### link to a page with a good view of tweets
Amanda's image This pdf is old: 
http://www.slaw.ca/wp-content/uploads/2011/11/map-of-a-tweet-copy.pdf



Let's look at our `taxday.jsonl` file again. Remember that after we
flatten them, our JSON 
files are line-oriented, ie: one tweet per line. Let's use `head -n 2 
source_data/taxday.jsonl > output_data/2-tweets.jsonl` to create a file 
with just two tweets.

If we use `!cat` to output that file to a Notebook cell, we see a real 
mess. Let's open the Jupyter graphical file viewer instead.

> ## Why not use BASH?
>
> We could use nano instead, and stay in our little shell window 
> with our hands on our keyboards.  However, we are going to spend
> our workshop in Jupyter to make our work more reproducible.
> 
> If you want to keep using nano, feel free.
> {: .source}
{: .callout}

Using either method, it's still difficult to tell what's going on. Can 
we even tell where one tweet ends, and the second begings?



# wc

Our most basic analysis can be done with a BASH command:
Demo `wc` for counting lines / tweets 



We can do this with our timeline file as well, but we need to `Flatten` 
it first.

By flattening Bergis' timeline and then looking at the file with `wc`, 
you can see that we retrieved 3171 of his tweets.

head: we can see those are super recent.

We can use `tail -n 2 sourcedata/ > output_data/bergistale.jsons` to see that
we have retrieved texts of his back to 2018.

Other things we can do: sentiment analysis (FORESHADOWING). See when he joined 
Twitter (hint: way before 2018)


How are the flattened and unflattened versions different? I’m thinking 
timeline jsonl looks a tiny bit different from searched/filtered tweets 
as jsonl. I can’t confirm yet. Timeline doesn’t really give a 
line-oriented set of tweets. <<< this is why we need flatten or csv

# Another Challenge
Use wc and head and tail to figure out how many Tweets you received from 
the account you harvested in Episode 2.


> ## First and last Tweets.
>
> Using the terminal, use the commands `head` and `tail` to 
> save the first 2 and last 2 tweets in `taxday.jsonl`.
> Download the file and view it in your web browser. 
> 1 How long is the time difference between the first and the last tweets?
> 2 Judging by these 4 tweets, do they arrive in chronological order?
> 3 Can you think of a more rigorous way to check?
>
> ~~~
> head -n 2 taxday.jsonl >  4tweets.jsonl
> tail -n 2 taxday.jsonl >> 4tweets.jsonl
> ~~~
> {: .source}
>
> > ## Solution
> >
> > 1 First Tweet in the file arrived Mon Apr 18 21:59:14, Final Tweet at Mon Apr 18 18:15:33. So these 
> > are Tweets span about 4 hours.
> > 2 Answer: They arrive in reverse-chronological, with the most recent Tweets are on top, oldest at the bottom.
> > ~~~
> > {"created_at": "Mon Apr 18 21:59:14 +0000 2022", "id": 1516174539742494723, ...
> > {"created_at": "Mon Apr 18 21:59:12 +0000 2022", "id": 1516174533732016132, ...
> > {"created_at": "Mon Apr 18 18:15:33 +0000 2022", "id": 1516118249443844102, ...
> > {"created_at": "Mon Apr 18 18:15:33 +0000 2022", "id": 1516118248110100483, ...
> > ~~~
> > Well?
> > Can we scroll through and examine it?
> > Is there the equivelent of a 'diff' command in Bash?
> > {: .output}
> {: .solution}
{: .challenge}

## Load our tweets into a pandas dataframe
As before, we are going to put out taxday tweets into a Pandas
dataframe for more analysis later. 

Here's a nice Pandas guide:
https://www.kdnuggets.com/2017/03/beginners-guide-tweet-analytics-pandas.html



{% include links.md %}

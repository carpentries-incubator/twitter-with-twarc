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
field, and you will encounter it frequently. On April 15th, 2022, we 
used twarc to search for all mentions of the hashtag `#taxday` (April 15th is
the deadline for Americans to file their annual income report).

Let's look at our `taxday.jsonl` file again. Remember that our JSON files are line-oriented,
ie: one tweet per line. Let's use `head -n 1 taxday.jsonl > 1-tweet.jsonl` to create a file
with just our first three tweets.

If we use `cat` to output that file to the screen, we see a real mess. Let's
open the file with a graphical text editor instead. 

> ## Why jump out of BASH?
>
> We should be using nano instead, but we don't have access to nano
> in our little shell window yet. 
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

There are many, many values attached to each Tweet. You will probably never use
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
  
(need to write a bit more about the first tweet)

### link to a page with a good view of tweets
This pdf is old: http://www.slaw.ca/wp-content/uploads/2011/11/map-of-a-tweet-copy.pdf


{% include links.md %}

> ## First and last Tweets.
>
> Using the terminal, use the commands `head` and `tail` to 
> save the first 2 and last 2 tweets in `taxday.jsn`.
> Download the file and view it in your web browser. 
> 1 How long is the time difference between the first and the last tweets?
> 2 Judging by these 4 tweets, do they arrive in chronological order?
> 3 Can you think of a more rigorous way to check?

> ~~~
> head -n 2 > 4tweets.jsonl
> tail -n 2 >> 4tweets.jsonl
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

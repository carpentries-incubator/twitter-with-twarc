---
title: "Working with our Tweets"
teaching: 0
exercises: 0
questions:
- "Why do we use jsonl, other than it being standard and popular?" 
- "Is there a more human-easy way to look at our data?"
- "Why json? ()"
- "How can I separate original content from retweets/replies?"
- "What are we using to view our data? "

objectives:

keypoints:
- "We can use nano or the built-in Jupyter file viewer to examine our data"
- "CSV’s are way more readable."
- "Converting to csv will often be your move, so you can visually inspect your data."

---

# Why is JSON data useful?

What are we using to view our data? 
Jupyter Built-in text viewer
Nano has been installed for us--it's a good editor to use because it has a little menu.
Use csv or xxx to make a browsable / human readable look at the tweets

## Can we find a spambot and follow it with:
--follow FOLLOW       limit filter to tweets from given user id(s)

This will be a fun experiment. who tweets a LOT?

When we have thousands of tweets: we need analysis tools:
Tweets vs. retweets

Lab Tasks
_ View JSONL in https://codebeautify.org/jsonviewer again
- Twarc1 vs twarc2 utilities
  - You can pip install twarc2 utilities
  - Upload twarc1 utilities from our setup or github

- Start running utils:
  - Tweets vs. retweets

Initial exploration is always:
- wc
- Originals vs. retweets
- Important to pay attention to during data analysis because you can end up with some very skewed results
Word count


Twarc-hashtags: is a built in extension/plug-in
The twarc1 utils folder:
https://github.com/DocNow/twarc/tree/main/utils
We will download at part of installation.

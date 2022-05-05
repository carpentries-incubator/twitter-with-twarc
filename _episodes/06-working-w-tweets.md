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

JSON has become an increasingly popular way to store and transfer data (especially data that is retrieved through APIs). It has a relatively concise and flexible data format that can be used with ease by many programming languages. In comparison to other data formats, such as XML, it's cleaner and responds faster to browser requests. 

The unfortunate thing about JSONs is that they are not structured in a way that humans are used to seeing data: in columns and rows or tables. 

Jupyter has its own built-in text viewer. (INSERT PICTURE AND NAVIGATE TO JUPYTER)
- Maybe insert a challenge right here where we can ask them to find something with in the data: text, number of retweets, username,...

Nano is also a good way to view JSON files because... It's already been installed for us. 

If you're finding it hard to process the information in these JSON files, don't worry! We're going to convert our data from a JSON to a CSV. (Write code up for process of conversion and take pictures. Before (JSON) and after (CSV). 

*I don't think we want them to put it in a different format than those.*

Should we add another challenge here to have them look for the emojis section? Or another portion of the csv to make sure they know how to navigate?


## Can we find a spambot and follow it with:
--follow FOLLOW       limit filter to tweets from given user id(s)

This will be a fun experiment. who tweets a LOT?

## When we have thousands of tweets: we need analysis tools

Back in Episode 1, we mentioned something referred to as 'utilities'. Now, we'll take a closer look at what those utilities are, how you use them, and why they are important to our Twitter data analysis and exploration. 

*Callout*
It's important to note that there are two sets of utilities: those used with twarc 1 and those used with twarc 2.
Also, add in link to guide Jon and I made in case they want example and explanations of twarc utilities. 

and you transferred the folder 'utils' that contains them into your Jupyter environment.
Looking at our csv, there's a LOT of retweets here (a tweet
that starts with a RT). We can run a Tweets vs. retweets (as a graph?)

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

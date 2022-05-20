---
title: "twarc Plus-ins and Utilities"
teaching: 0
exercises: 0
questions:
- "How can we look at our tweets more easily" 
- "What's the difference between old twarc and twarc2?"
- "How can I separate original content from retweets/replies?"
- "What are we using to view our data?"

keypoints: 
- "CSV’s are way more readable in Jupyter."
- "twarc1 has a folder of python scripts for basic analysis that still work, but you need to retrieve them."
- "twarc2 has plug-ins that need separate installation"
---


Jupyter has its own built-in viewer that works great for csvs. (INSERT PICTURE AND 
NAVIGATE TO JUPYTER) -

Maybe insert a challenge right here where we can ask them to find 
something with in the data: text, number of retweets, username,...

If you're finding it hard to process the information in these 
JSON files, don't worry! That's why we have our jsonl > csv > 
dataframe pipeline.


Should we add another challenge here to have them look for the 
emojis section? Or another portion of the csv to make sure 
they know how to navigate?



## When we have thousands of tweets: we need analysis tools

Back in Episode 1, we mentioned something referred to as 
'utilities'. Now, we'll take a closer look at what those 
utilities are, how you use them, and why they are important to 
our Twitter data analysis and exploration.

*Callout* It's important to note that there are two sets of 
utilities: those that came from twarc 1 that we put in our 
jupyterlab ourselves, and those that get pip installed on top
or twarc2

The twarc1 utilities are python files that we uploaded as part 
of setup. twarc2 plug-ins, like twarc-csv come along with the 
twarc installation, but need to be installed separately 
(that's why we did `!pip install twarc-csv` earlier)

# emojis

Sometimes you can tell the overall 'emotional tone' of a dataset
by looking at its most used emojis. Do we think that taxday
or kittens are going to have more positive emojis?

* code *
make csv's with the top emojis for both taxday and kittens


* callout
link to github guide 
Jon 
and I made in case they want example and explanations of twarc utilities.

The twarc1 utils folder:
https://github.com/DocNow/twarc/tree/main/utils
We downloaded as part of installation.

## Tweets vs. retweets

Looking at our csv, there's a LOT of retweets here (a tweet that 
starts with a RT). We can run a Tweets vs. retweets (as a graph?)


Originals vs. retweets is such a good metric to have, we 
should add it to our workflow:

1. test search Twitter
1. download data
1. flatten in necessary
- wc: see how many you got
- csv: to make it readable
- determine date range
- Originals vs. retweets

# A simple view of results
- Start running utils:
!python utils/wall.py raw_data/taxday.jsonl > output_data/taxday_wall.html

taxday might be too big for wall.


Twarc-hashtags: is a built in extension/plug-in



## Can we find a spambot and follow it with:
--follow FOLLOW       limit filter to tweets from given user id(s)

follow was a flag on twarc1's filter to find all mentions of a user. 
what's the twarc2 equivelent?

If we can find someone who 
tweets alot, we can see who they are 
@-ing on their timeline. OR: see @'s as part of a search/stream



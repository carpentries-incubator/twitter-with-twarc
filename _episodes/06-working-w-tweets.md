---
title: "Twarc Plus-ins and Utilities"
teaching: 0
exercises: 0
questions:
- "How can we look at our tweets more easily"
- "What's the difference between the first release of twarc and twarc2?"
- "How can I separate original content from retweets/replies?"

keypoints:
- "CSV’s are way more readable in Jupyter."
- "twarc1 has a folder of python scripts for basic analysis that still work, but you need to retrieve them."
- "twarc2 has plug-ins that need separate installation"
---

## When we have thousands of tweets: we need analysis tools

- -
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
- -

Back in Episode 1, we mentioned something referred to as
'utilities'. Now, we'll take a closer look at what those
utilities are, how you use them, and why they are important to
our Twitter data analysis and exploration.

It's important to note that there are two sets of
utilities: those that came from the first iteration of twarc (files in the "utils" folder), and those that get pip installed on top
of twarc2.

Twarc2 plug-ins come with the initial twarc2 installation, but needs to be installed separately. For example, `twarc-csv` is a twarc2 plugin,
but we needed to pip install `twarc-csv` before we could use it in our notebook.

The utilities from the first release of twarc, which we'll simply refer to as "twarc 1", are python files that we uploaded as part
of setup. They should now be in your "utils" folder. These utilities provide useful data-processing tools that we can use on Twitter data that have been harvested using twarc2 commands.

## Utilities: emojis

The first utility from twarc1 reads emojis. You will need to pip install this utility into the notebook before we may use it.

~~~
!pip install emoji
~~~
{: .language-bash}

~~~
import emoji
print(emoji.emojize('Hello :earth:!'))
~~~
{: .language-python}

~~~
Hello 🌎!
~~~
{: .output}

While we only need to pip install emoji into our environment once, you will need to import whenever you open a new notebook.
We can use emojis to get a count of emojis from a set of tweets, and these results are kept in a text file.

~~~
!python 'utils/emojis.py' 'raw_data/CapitolRiotTweets_hydrated.jsonl' > 'output_data/capitol_emotes.txt'
~~~
{: .language-bash}

Note: the language for using this is BASH, not python. The emojis is python-based, but is intended to be ran as a BASH command.

> ## Challenge: Comparing hashtags
> Sometimes you can tell the overall "emotional tone" of a dataset
> by looking at its most used emojis. Do we think that taxday
> or kittens are going to have more positive emojis?
>
> > ## Solution
> > We may use emojis on both data gathered with twarc1 and twarc2.
> > ~~~
> > !python 'utils/emojis.py' 'raw_data/taxday.jsonl' > 'output_data/taxday_emotes.txt'
> > ~~~
> > {: .language-bash}
> >
> > ~~~
> > #catsofinstagram was harvested with the twarc2 command, timeline
> > (FIXME)
> > ~~~
> > {: .language-bash}
> >
> {: .solution}
{: .challenge}

# Utilities: wall

(FIXME) What wall command does
(FIXME) Why we need to flatten

~~~
!twarc2 flatten 'raw_data/CapitolRiotTweets_hydrated.jsonl' > 'output_data/capitol_flat.jsonl'
~~~
{: .language-bash}

~~~
!python 'utils/wall.py' 'output_data/capitol_flat.jsonl' > 'output_data/capitol_wall.jsonl'
~~~
{: .language-bash}


(FIXME) Twarc-hashtags: is a built in extension/plug-in


(FIXME) If we can find someone (such as @tinycarebot) who
tweets alot, we can see who they are
@-ing on their timeline. OR: see @'s as part of a search/stream

# Utilities: retweets

We may get data on the retweets of one or more tweets. Recall that a retweet is when a Twitter account shares the Tweet of a different Twitter account.

![tiny care bot's tweet that has three retweets](../fig/tcb_tweet.png)

This tweet has three retweets. We are able to compile data on the Twitter accounts that have retweeted the above tweet. By using the twarc1 utility, `retweets`, we can gather this information in a line-oriented json file.

~~~
#!python 'utils/retweets.py' ...
(FIXME)
~~~
{: language-bash}

Another way we can gather data on the user accounts of the retweeters is by using a twarc2 command. First, we will need to get the tweet's numeric identifier. One way we can get a tweet's ID is by looking at the url of the tweet. In this case, the tweet's ID is 1522543998996414464.

~~~
!twarc2 retweeted-by 1522543998996414464 > 'raw_data/tinycarebot_rtby.jsonl'
~~~
{: .language-bash}

## Tweets vs. retweets

(FIXME) Looking at our csv, there's a LOT of retweets here (a tweet that
starts with a RT). We can run a Tweets vs. retweets (as a graph?)

(FIXME) Originals vs. retweets is such a good metric to have, we
should add it to our workflow:

(FIXME)
1. test search Twitter
1. download data
1. flatten in necessary
- wc: see how many you got
- csv: to make it readable
- determine date range
- Originals vs. retweets

## Followers

<<<<<<< HEAD
(FIXME) Even 5 takes a long time to run. We could try to expand on
~~~
!twarc2 followers --limit 5 tinycarebot >  'raw_data/tcb_followers.jsonl'
~~~
{: .language-bash}
=======
Challenge: Boolean and: how to feed search multiple ID’s? This is a challenge
about using twitter advanced search syntax. Can we distinguish between AND’s and
OR’s?

>>>>>>> f4167cde944f01c8c0bdc3b5e5639a57b3a2b1db

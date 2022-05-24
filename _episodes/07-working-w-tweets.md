---
title: "Twarc Plugins"
teaching: 15
exercises: 5
questions:
- "What other harvests are available?"
- "Are there more twarc2 plugins?"
- "How can I separate original content from retweets/replies?"

keypoints:
- "twarc2 has plug-ins that need separate installation"
- "The network plug-in shows us how tweeters are related to each other"
- "twarc1 has a folder of python scripts for basic analysis that might still work."
---

# Other Harvests
Twarc2 has commands to retrieve entire conversation threads, as well as the 
retweets of one or more tweets. Recall that a retweet is when a 
Twitter account shares the Tweet of a different Twitter account.

![tiny care bot's tweet that has three retweets](../fig/tcb_tweet.png)

This tweet has three retweets. We can retrieve those:

We will need to get the tweet's numeric identifier. We 
can see the tweetID by looking at the url of the tweet. In this case, the tweet's ID 
is 1522543998996414464.

~~~
!twarc2 retweeted-by 1522543998996414464 > 'raw_data/tinycarebot_rtby.jsonl'
~~~
{: .language-bash}

This gives us the profiles of the three twitter accounts . From there
we can go on to harvest their timelines to see what they are up to.


## Followers
Not only can we see everyone who has retweeted another tweet, we can also
find all the followers of a given account.

@tinycarebot is very popular, so let's get just a few of their followers:
~~~
!twarc2 followers --limit 5 tinycarebot >  'raw_data/tcb_followers.jsonl'
~~~
{: .language-bash}


### When we have thousands of tweets: we need analysis tools
So that's one tweet, and one account's followers. But we have harvested thousands of tweets,
how can we get a grip on them?

A few [more twarc2 plugins](https://twarc-project.readthedocs.io/en/latest/plugins/)
are available to help get this work done.

twarc2 plug-ins, like csv that we did earlier, need to be installed separately. 
In this episode, we will look at twarc-hashtags and twarc-network

First you need to `pip install` in BASH

~~~
!pip install twarc-hashtags
!pip install twarc-network
~~~
{: .language-bash}

### Most seen hashtags
When we run hashtags on our `hashtagcats` dataset, we should see the hashtag 
we search for first. Our other results make sense as well. We see a lot of dogs and Japanese 
cropping up. In case you didn't know it, Internet cats are huge in Japan.

#### Top hashtags
~~~
!twarc2 hashtags raw_data/hashtagcats.jsonl output_data/hashtagcats_hashtags.csv
~~~
{: .bash}

![screenshot showing top 20 hashtags](../fig/cat_hashtags.png)


> ## Challenge: Look for surprises
>
> Run hashtags on two of your other datasets.
>
> Are there tags that surprised you?
> Look at that individual tweet and figure out if that context helps you
> understand why that unanticipated hashtag is there.
>
> > ## Solution
> >
> > I looked at people who mentioned UCSB Library.
> >
> > ~~~
> > ![Image showing top 13 hashtags](../fig/mentions.png)
> > ~~~
> > {: .output}
> >
> > #FIXME what sort of challenge can we have?
> > library mentions got nuked because nobody tweets @at the library
> >
> >
> {: .solution}
{: .challenge}


## Interpreting the network results

We call network the same way we called hashtags

~~~
> !twarc2 network raw_data/hashtagcats.jsonl output_data/hashtagcats_network.html
~~~
{: .language-bash}

The built-in web viewer ain't so hot, so download that html file to view the network on 
your own computer. Chrome works fine, and it's best to make the diagram fullscreen. We can 
see: 
- the largest central cluster around the account @catsofinstagram 

- a corporate entity (litter box company in the upper right) shows up, and that a big 
  sub-network exists

- neighborhoods of users, such as those around kiko1123215 in the
  image below. Kiko is nearby, but separate from, the 
  @catsofinstagram twitter account.

![portion of a network diagram with a central node kiko11232015 off to the
side of the main cluster of the account @catsofinstagram](../fig/cat_network.png)



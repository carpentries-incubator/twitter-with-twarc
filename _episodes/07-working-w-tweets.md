---
title: "Twarc Plugins"
teaching: 15
exercises: 5
questions:
- "How can we look at our tweets more easily"
- "Are there more twarc2 plugins?"
- "How can I separate original content from retweets/replies?"

keypoints:
- "twarc2 has plug-ins that need separate installation"
- "The network plug-in shows us how tweeters are related to each other"
- "twarc1 has a folder of python scripts for basic analysis that might still work."
---

## When we have thousands of tweets: we need analysis tools

twarc2 plug-ins like csv need to be installed separately. 
In this episode, we will look at twarc-hashtags and twarc-network

A few [more twarc2 plugins](https://twarc-project.readthedocs.io/en/latest/plugins/)
are available.

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
> > I looked at the Library's timeline to see how it uses hashtags.
> >
> > ~~~
> > ! twarc2 hashtags xxx.jsonl
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

# Retweets

We may get data on the retweets of one or more tweets. Recall that a retweet is when a 
Twitter account shares the Tweet of a different Twitter account.

![tiny care bot's tweet that has three retweets](../fig/tcb_tweet.png)

This tweet has three retweets. We are able to compile data on the Twitter accounts that 
have retweeted the above tweet. 

Another way we can gather data on the user accounts of the retweeters is by using a 
twarc2 command. First, we will need to get the tweet's numeric identifier. One way we 
can get a tweet's ID is by looking at the url of the tweet. In this case, the tweet's ID 
is 1522543998996414464.

~~~
!twarc2 retweeted-by 1522543998996414464 > 'raw_data/tinycarebot_rtby.jsonl'
~~~
{: .language-bash}

## Followers

Another form of Twitter data is a follower list. twarc allows
us to get a follower list:
~~~
!twarc2 followers --limit 5 tinycarebot >  'raw_data/tcb_followers.jsonl'
~~~
{: .language-bash}


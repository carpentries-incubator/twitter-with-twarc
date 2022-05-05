---
title: "Ethics & Twitter"
teaching: 0
exercises: 0
questions:
- "Can I avoid seeing hate speech and unsettling imagery and still analyze twitter?"
- "What are some privacy or other ethical issues that you need to keep in mind when harvesting tweets with twarc?"
- "How much personal information can we actually gather about a user given our twarc scrape?"
- "What are some inappropriate things to do with twarc?" <- ???? 
objectives:
- "Discuss the privacy or ethical concerns surrounding tweet harvesting. (FIXME)"
keypoints:
- "'Distance reading' is analyzing big full-text data without a human consuming the words"
- "Robot detection, archives, deleted accounts"
---

# Let's Get Ethical



## Misinformation

Something about social media as a tool for people with certain motives. 
I wonder if theres a Parler Dataset on Kaggle? Or do you think that might violate the Carpentries code of conduct (too risky?)? 

> ## Challenge: January 6 Insurrectionists
>
> After the US Capitol riot, a user on kaggle captured 80,000
> Tweets from people associated with that day's events, concentrating
> on accounts from those protesting / rioting.
> 
> This kaggle user, in the public interest, stored the full content of
> these Tweets as a .csv. The best practice would be to save only a 
> dehydrated set of tweets. However, in this instance, we can use this 
> person's conscientious objection to social norms and Twitter's
> Terms-of-Service to ask whether or not any of this is in the
> public good or an acceptable topic of research.
>
> Using the file [dehydrated_Capitol_Rioters.txt](../data/dehydratedCapitolRiotTweets.txt), determine how many
> Tweets were in the archive, and how many remain on Mr. Musk's new
> acquisition. 
> {: .source}
>
> > ## Solution
> > On first run through, only 10 of the first 999 tweets remain.
> > This indicates that a huge proportion of this dataset has
> > been deleted or restricted by Twitter.
> > {: .output}
> {: .solution}
{: .challenge}


## GDPR 

Something about GDPR. 

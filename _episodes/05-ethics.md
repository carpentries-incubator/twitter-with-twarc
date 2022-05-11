---
title: "Ethics and Twitter"
teaching: 0
exercises: 0
questions:
- "Can I avoid seeing hate speech and unsettling imagery and still analyze twitter?"
- "What are some privacy or other ethical issues that you need to keep in mind when harvesting tweets with twarc?"
- "How much personal information can we actually gather about a user given our twarc scrape?"
- "What are some inappropriate use cases for twarc?"
key points:
- "Discuss the privacy of ethical concerns surrounding tweet harvesting. (FIXME)"
keypoints:
- "'Distance Reading' is analyzing big full-text data without a human consuming the words"
- "Robot detection, archives, and deleted accounts"
---


# Kittens and Elephants
Maybe you think we have being coy, but here is where we acknowledge the 800-pound
elephant in the room. Twitter is not all kittens and rainbows. As we all know, 
hashtag-#rainbow will lead us into LGBTQ-issues. We've already told you that twarc
was born of the Black Lives Matter movement. 

Both of these issues, 

# Let's Get Ethical

There are multiple ethical fields to consider when using and presenting Twitter 
data. In this lesson, we will be focusing on two issues: consent, misinformation, 
and core legal practices as it relates to archiving data.

## Misinformation

Something about social media as a tool for people with certain motives. I wonder 
if theres a Parler Dataset on Kaggle? Or do you think that might violate the 
Carpentries code of conduct (too risky?)?

## Avoiding the ickiness
What is distance reading and how does it relate to social media research?


Rehydrate: get an archive from the Jan. 6 
archive? 
← -1 from Amanda: may contain inappropriate content for a carpentry 
workshop Analyze to see how much got deleted as Twitter expunged extremists? 
Are 
the archives dehydrated? Can you get the fulltext from twitter? 
If not, from 
where? 
Kaggle has full text csvs One with a cc license. One with a copyright. 
Tweetsets GWU: https://tweetsets.library.gwu.edu/ Who got deleted? Are they real 
people? 

Is the data really deleted? 
https://media.nature.com/lw800/magazine-assets/d41586-021-00257-y/d41586-021-00257-y_18832182.png 
Challenge: Boolean and: how to feed search multiple ID’s? This is a challenge 
about using twitter advanced search syntax. Can we distinguish between AND’s and 
OR’s? 

Challenge: Where does Jules B. live? Zoom poll? 
which of the following 
would be inappropriate uses of twitter data? Use Rehydration to find deleted 
accounts (violators, robots, etc.) 

Search for individual tweeterIDs? Find one that definitely has been 
deleted? There is only a tiny little fraction of the content still available from 
twitter. (peg the number for the script?)


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



## Personally identifable information
We get a lot of personal information when we gather tweets. Enough to create 
personalized ads, right? 

We can determine a users’ approximate location, what 
they like, their beliefs, etc. 

Yes What is distance reading and how does it 
relate to social media research? 
One benefit of distance reading is that it prevents us 
from seeing unwanted images and language that we might see when simply doom 
scrolling twitter on our phones. 

## Authorship, the GDPR, and the Right to be Forgotten

Twitter is an unusual social media platform for a number of reasons, not the
least interesting of which is that you, the user, maintain ownership of your
tweets. You are the author, and as an author you have both copyrights and
moral rights coming to you.

Copyrights prevent some horrible troll from compiling your tweets together into a 
publication and monetarily profiting from them. That said, some authors do not 
have any copyrights. For example, POTUS is an American government employee, 
therefore the property is in the Public Domain. 

Laws vary greatly by country, so don't get American librarians started on 
the Queen's copyrights over Canadian government data.

Moral rights are more complicated. Laws vary greatly by country--even moreso than 
copyright. In the European Union, authorship includes the right to un-publish,
in other words, the right to be forgotten. Twitter, very cleverly, preserves this
right by letting us delete our tweets.


Something about GDPR.

GDPR defines Personal data as:

> ...Personal data are any information which are related to an identified or identifiable natural person.
>
> The data subjects are identifiable if they can be directly or indirectly identified, especially by reference to an identifier such as a name, an
> identification number, location data, an online identifier or one of several special characteristics, which expresses the physical, physiological,
> genetic, mental, commercial, cultural or social identity of these natural persons...

> ## Discussion: Personal Data
>
> Do you think that Twitter data should be treated as personal data?
> What did you consider when making this judgment?
>
{: .discussion}

## User Content, Re-use, and Consent

Twitter users have various options of privacy over their content and profile. 
Some of these options include that their profiles do not show up in web searches 
and that their content is hidden only to followers. While these options are 
available to users, it does not have any retroactive effect on what has already 
been collected. That is, if a user's tweets are collected and the user deletes 
their Twitter account, their content is still in someone else's database for use. 
When creating an archive of data, we must understand that the creators behind 
these tweets have not consented to their content being kept for years from now.

Furthermore, Twitter users who do not put a restriction on what content may be 
viewed may also not be aware of who has access to data collection; and what they 
may do with it. A study from Cardiff University found an association between 
concern for anonymity and sexual orientation, ethnicity and gender. Twitter data 
may contain identifying demographic information, identifying associations or 
membership, and expression of a very personal nature. These are items that users 
may want to protect. A basis for ethical consideration is not only to conduct 
good and upholding science, but also to minimize risk or harm during any of the 
study's data collection and publication.


## Citations

---
title: "Data Management"
teaching: 10
exercises: 5
questions:
- "What are some best practices for handling our data 'for the long term'?"
objectives:
- "Twitter has a Terms of Service for data"
- "Long-term storage of id-only datasets is a good method"
keypoints:
- "Dehydrating your tweets solves a lot of issues"
---

# Now What?
You have gathered timelines on individuals going back years.

You have harvested data from the Twitter
livestream and searched back over the previous six days.

You have determined the relative sentiment of several different
Twitter datasets, examined the top hashtags, the most frequently
used words, and the proportion of tweets to retweets. 

You made network diagrams!

Now it's time to wrap up your data for long-term storage. But how?

## Twitter's TOS and the EU's GDPR
Twitter the corporation allows users to delete (but currently not
edit) their own content. And when the European Union created its
General Data Protection Regulations, it enshrined in law the 'right
to be forgotten.' 

And so, to respect Twitter's Terms of Service as well as what is widely
considered to be a human right, the best practice is to dispose of your
full-data tweets and leave only the tweetID's and the end results
of your analyses.

We explored the opposite of this idea earlier in (Ethics
and Twitter)[05-ethics] when we hydrated tweets that had 
been collected after a serous event. We found that many of the 
malicious actors and bots are no longer available in the Twitter
archive. 

However, when we do our research, unless perhaps we are specifically 
looking only at non-person actors or public figures, when our 
research is complete we should always dehydrate our dataset for 
long-term archiving, or before we share data with people outside of 
our immediate research team.

~~~
! twarc2 dehydrate raw/hashtagcats.jsonl output_data/dehydrated_cats.txt
~~~
{:.bash}



> # Challenge: hydrated or de-hydrated?
> 
> Was making you log-in to get full-text gas-price tweets a good enough
> protection for our #gasprices dataset?
> 
> Which of our datasets would you feel comfortable creating an 
> official, UCSB-sponsored archive?
> -	Bergis Jules' timeline? 
> -	Library mentions? 
> -	Library timeline? 
> -	full text Capitol riots tweets?
> -	#catsofinstagram?
> > ## Solution
> > you decide!
> >
{: .challenge}

## DocNow's new tool for consent. 

DocNow released a [new tool](https://www.docnow.io/docnow-app/) that allows for the appraising, collecting, and gathering of consent for social media archives. 

User Content, Re-use, and Consent Twitter users have various options of privacy over their 
content and profile. Some of these options include that their profiles do not show up in 
web searches and that their content is hidden only to followers. While these options are 
available to users, it does not have any retroactive effect on what has already been 
collected. That is, if a user’s tweets are collected and the user deletes their Twitter 
account, their content is still in someone else’s database for use. When creating an 
archive of data, we must understand that the creators behind these tweets have not 
consented to their content being kept for years from now.

Furthermore, Twitter users who do not put a restriction on what content may be viewed may 
also not be aware of who has access to data collection; and what they may do with it. A 
study from Cardiff University found an association between concern for anonymity and sexual 
orientation, ethnicity and gender. Twitter data may contain identifying demographic 
information, identifying associations or membership, and expression of a very personal 
nature. These are items that users may want to protect. A basis for ethical consideration 
is not only to conduct good and upholding science, but also to minimize risk or harm during 
any of the study’s data collection and publication.

Citations


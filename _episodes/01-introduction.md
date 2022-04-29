---
title: "Introduction"
teaching: 0
exercises: 0
questions:
- "What is a tweet?"
- "What is TWARC?"
- "What is an API and how can I get started?" 
objectives:
- "First learning objective. (FIXME)"
- "How is a tweet considered to be data?"
- "How to access the twitter API"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

# Learning to Speak Twitter

Twitter is a social media platform where users post short messages, pictures, news stories, and other content to be viewed by others. It allows people from all over the world to interact with each other almost instantaneously. 

<img src="../fig/twitter.png" alt="Twitter Explore Page" width = "300" height = "400"/>

If you've never used Twitter before, the language used, in addition to being NSFW, can be totally cryptic. Beyond "@ing people" and "hashtags", the users themselves have created Twitter-wide standards, and Twitter is also filled with subcommunities who use their own lingo.

Twitter has its own <a href="https://help.twitter.com/en/resources/twitter-guide/twitter-101/speak-the-language-of-twitter-twitter-help">getting started guide.</a>

> ## Challenge
Throw a few terms into the etherpad

This is a not too awful guide:
https://www.lifewire.com/twitter-slang-and-key-terms-explained-2655399


{% include links.md %}

# API: A Complicated Topic and a (mostly) Easy Tool

API is an abbreviation that stands or Application Programming Interface. It allows computers or applications to communicate with one another without requiring users to code operations from scratch. APIs allow you to use abstraction, because similar to how you don't need to know the engineering behind your shower in order to use it, you don't need to understand the code behind APIs in order to fetch data. 

Formally defined, an API is a set of commands, functions, protocols, and objects used by programmers to create software or to interact with external system.

## Common Analogy

Imagine yourself sitting at a table in a restaurant. The waiter comes to your table and you order from a set list of items on the menu. The waiter then takes your order to the chef/kitchen crew who put together different meals and drinks for your table. The waiter then takes your order to your table. 

Here are the key players in our analogy:
1. Customer - you as the user
2. Menu items - the commands and operations you can pass to an API in order to retrieve information
3. Waiter - the API that delivers your information request to the system, and then your resulting dataset to you 
4. Chef/Kitchen crew - the external program or webserver that has the information you seek

You can visualize this anaolgy <a href="(https://www.mulesoft.com/resources/api/what-is-an-api)">here</a>.

> ## APIs are not Webscraping
The biggest difference between APIs and Webscraping is the retrieval method. With APIs you are using a system preset by the website you are trying to access the data from (Twitter, YouTube, Spotify, ...). 


# Twarcing

You may be asking, "What is twarc?" or, "Why do all things involving Twitter have to start with a 'tw'?".

Twarc is one of the APIs used to retrieve data from Twitter.




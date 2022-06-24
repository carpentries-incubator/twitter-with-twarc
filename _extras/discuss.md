---
title: Discussion
---
# Twitter and twarc Key Points
By the end of this lesson, you will know the following:

- How to use a Python application with a public API
- How to look at JSON encoded data in a human-readable way using your web browser, etc.
- Learning to examine big data files with an emphasis on data cleaning and exploration
-- How to handle “not human readable data” / “big data”?
- Know where to look for help on FOSS git-based projects
- Be familiar with Twitter data and assembling / harvesing datasets with twarc

# The Narrative

In episode 1, we learn a little bit about Twitter. It is a ubiquitous part of our
world, and one that allows us to access its platform via an API. We will use twarc,
a Python 'wrapper' for the Twitter API.

In episode 2, we learn how to navigate a Jupyter Notebook and send BASH commands from
inside of a notebook. We configure our twarc application, and test it out by harvesting
the timeline of Bergis Jules, one of the creators of twarc and driving force behind
Document the Now.

In episode 3, we make a few very small files, and take a look at several ways to 
take a look at JSON and the information that comes in a tweet. JSON is an entire world
of name:value pairs. Tweets are primarily integers, dates, and strings. We gather
tweets that have used a specific #hashtag during the past 6 days. 

In episode 4, different Twitter API endpoints are explored. Beyond timeline, we can 
search for the number of times certain things happen on Twitter via the `counts` enpoint.
`Search` and `Stream` are the other two endpoints on which we will concentrate for the
rest of the workshop. The `#catsofinstagram` hashtag appears. We will manage our quota a
little bit.


{% include links.md %}

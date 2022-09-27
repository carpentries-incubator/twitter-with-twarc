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
- Understand the importance of following a standard workflow when 

# The Narrative

In episode 1, we learn a little bit about Twitter. It is a ubiquitous part of our
world, and one that allows us to access its platform via an API. We will use twarc,
a Python 'wrapper' for the Twitter API. Wrappers help those of us who are novice
coders to use an API we would not be able to code against directly.

In episode 2, we learn how to navigate a Jupyter Notebook and send BASH commands from
inside of a notebook. We configure our twarc application, and test it out by harvesting
the timeline of Bergis Jules, one of the creators of twarc and driving force behind
Document the Now. *this should be re-written to use `sample` as the first test of
the twarc install.

In episode 3, we make a few very small files, and take a look at several ways to 
take a look at JSON and the information that comes in a tweet. JSON is an entire world
of name:value pairs. Tweets are primarily integers, dates, and strings. We gather
tweets that have used a specific #hashtag during the past 6 days. 

In episode 4, different Twitter API endpoints are explored. Beyond `Sample`, we can 
search for the number of times certain things happen on Twitter via the `counts` endpoint.
`Search` and `Stream` are the other two endpoints on which we will concentrate for the
rest of the workshop. The `#catsofinstagram` hashtag appears. We will manage our quota a
little bit. We start making dataframes and articulate our standard workflow.

We plan to nuke episode 5 and insert an 'ethical moment' into each episode. Ep. 5 itself
will prepare the Jan 6 datafile (or whatever we replace it with). We will add a column to
a dataframe and start populating that with SH-A classifications.

Episode 6 describes the difference between search and stream and rather exhaustively
goes over Boolean searching. If you stream, you should clean up after yourself. There 
are Grumpy Cats and Doja Cat

In episode 7 we look at twarc2 commands to gather conversations and follower networks.
We try to identify SH-A robots who might be following other robots. We use Python to
analyze the original-tweet:re-tweet ratio. That gets tacked on to our standard research
workflow.

Episode 8 returns to NLP and we assess the sentiment and the objectivity of our 
datasets. We can guess that the Capitol Riots and gasoline prices are going to be
very subjective and very negative datasets, while fluffy kitty cats will trend positive.
We had wanted to insert an emoji exercise into this episode.

Episode 9 applies dehydrating and hydrating datasets for long term storage and goes
over appropriate times when it would be acceptable to save and share full datasets.
A final challenge here could be to see how many of our dataframe with a SH-A column
is populated and see if we can hand-apply tags to the remainder?

Not Mapping Twitter is a long awaited articulation of a ppt we did about 6 years
ago. There's a brief outline there.

{% include links.md %}

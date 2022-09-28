---
title: "Instructor Notes"
---

# Ep. 1 Introduction to Twitter
* 

# Ep. 2 Getting familiar with JupyterLab

* We harvest the bjules timeline in order to test the installation
* We do first and last with bjules and hashtag gas.
* Generally, this is too long. This isn't a Jupyter lesson (or could it be?)
* After configuring twarc in jupyterlab, helpers can help struggling learners on the twarc2 
  configuration while the instructor may go over the remaining episode content.
* We've written the lesson using @ecodatascience as the  solution to the '2 Timelines' 
  so if you do that as an instructor, subsequent code should run as is. We plan to
  replace @ecodatascience with @bergisjules in subsequent episodes in order to simplify things.

# Ep. 3: Anatomy of a Tweet

* The key point is to show a little bit of json and talk people into
  immediately converting to csv and dataframe
* The difference between timelines and search/filter datasets needs
  to be made explicit here.

# Ep. 4: Twitter Public API

* @bjules vs #catsofinstagram. What's the difference difference between a 
  timeline and a sample/search capture?
* @ucsblibrary is going to be edited out
* The final challenge in episode 4 is to live harvest a dataset
  using a 'cute' hashtag. You may wish to pre-harvest
  a dataset. Beware of improvising: you may get results that you
  don't want on your screen.
  
# Ep. 5: Ethics

# Code
* [This Jupyter Notebook](../code/TwarcWorkshop.ipynb) has 
  most lines that use quota or take a long time to run  
  are commented out.

* [This notebook will](../code/TwarcWorkshop_with_harvests.ipynb) run 
  the workshop from start to finish AND consume quota, assuming
  you have downloaded the appropriate data from the setup page.

* [Halfway notebook](../code/workshop_halfway.ipynb) is a natural
  starting point for day two if you split this lesson in half.
  It runs and leaves you with three dataframes in memory.


{% include links.md %}

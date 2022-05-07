---
title: "Analysis Tools"
teaching: 0
exercises: 0
questions:
- "What else can we do with our tweets?"
- "How can I analyze my tweets beyond what twarc offers?"
- "Is it possible to tell if tweets are expressing positive or negative feelings?
"


objectives:
- "distinguish between twarc1 .py utilities and twarc2 plug-ins"
- "do a bit more Python with our Jupyter notebook"
- "introduce sentiment analysis"
keypoints:
- "What else? (FIXME)"
---

# 

Twarc utilities
We already did tweets/retweets
Pull out Emojis only?
  you can visually see sentiment there.
What else from the old slide-deck must we cover?
Twarc2 extensions
Network (very slow. Demo only? Pre-worked example?)

Python
We can use the sentiment analysis built into python
But we need plain text.

# break tweets test column into a list, then .join into one long string 
kittens_string = ' '.join(kittens_df['text'].tolist())
# turn the string into a blob
kittens_blob = TextBlob(kittens_string)
# get the sentiment
kittens_blob.sentiment

Challenge: sentiment of taxday.jsonl


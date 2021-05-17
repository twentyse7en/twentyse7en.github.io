---
title: 'Recommendation Engines - Part 1'
date: 2021-05-17
layout: post
comments: false
tags:
  - RecommentionEngines
  - Data
---

## Introduction

There is a mandatory *Final Year Project* in our curriculam. Our team consist
of 4 people and we had very interesting ideas, but too sci-fi (Realtime stock
market analysis, Workout assistance with computer vision). Finally we ended up
with a project to explore Book Recommendations.

In this blog we will explore basic idea about recommendation engine.

## Recommendation Engine - 101

Recommendation engine are every where, Netflix, Spotify, Youtube (recommends
an unrelated video posted 8 years ago, atleast for me). It is very crucial tool
to enhance the user experience. Let's explore the basics of recommendation engine.

### Content Based Filtering

Content Based Filtering uses the metadata of items that user already likes
. For example if you like movie [The Dark Knight](https://www.imdb.com/title/tt0468569/)
the metadata includes `{"Director": "Christopher Nolan", "Genre": ["DC", "Comic", "Superhero"]}`
So we can use this data to recommend more movies of  Christopher Nolan, movies
based of DC, comic, superhero etc. Also we can use the user metadata such
as age, gender, location.

### Collaborative Filtering

Collaborative filtering uses similarities between users and items
simultaneously to provide recommendations. For example, If you and your
friend has similar taste in movies, he can recommend movies he likes, most
probably you might also like that movie. This can further divide into two.
- Explicit Feedback : User provide positive or negative feedback. Like/Dislike
  in youtube, review stars in amazon.
- Implicit Feedback : Most of the users might not like or dislike in youtube,
  even if they are interseted or not interseted. If they skip the video after
  few minutes, this could be a negative feedback, like that we can infer the
  feedback from other attributes.
We can look in more details in upcoming blogs.


## Reference
1. [DeepLearning@Institut Polytechnique de Paris](https://github.com/m2dsupsdlclass/lectures-labs)
2. [CS246: Mining Massive Data Sets@stanford](https://web.stanford.edu/class/cs246/slides/07-recsys1.pdf)


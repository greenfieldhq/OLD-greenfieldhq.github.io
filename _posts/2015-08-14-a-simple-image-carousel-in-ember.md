---
layout: post
category:
tagline: ""
tags:
title: "A simple image carousel in Ember"
description: How to build a simple modal in Ember
author: vikram_ramakrishnan
---
{% include JB/setup %}

# Blog Post Outline [DRAFT]

## There are so many libraries out there that do carousels. Write do we need to write your own?!

You're probably familiar with an image carousel. It's a little tool that lets you display some pictures on a page rotating through one another. The type we'll deal with here is the kind that lets us click to determine which picture we want to see:

[Example]

Now, there are tons of examples of these in JQuery: [Jssor](www.jssor.com/), [Owl Carousel](owlgraphic.com/owlcarousel), [Slick.js](http://kenwheeler.github.io/slick/) and many, many others. All of these are excellent tools, but as Ember developers, do we really need them? Let's ask the question another way? Is a native image carousel a perfect use case for Ember?

#### Stop using JQuery libraries for things Ember lets you do for free!

- Why do we want to do this?
- What does Ember give us?
- This is what ours will look like (animated gif)

## Alright, I'm convinced! How are we going to do this?

- First off, we'll need some kind of backend (do we?) and I don't think this worth spinning up a whole rails api or anything for this. We can look at Mirage. Don't want to get into all the details of Mirage (here are some blog posts), but we can get it setup and go with it.
- Pseudo-english-ed version of how we'll build this; why flow control will be important
- Addons we'll need for this project: font awesome & ember truth helpers

## Is there anything conceptually that would help us out here?

- pod structure
- promises

## Implementation

- code

## Stuff to try out

- Add animations! (check out liquidfire)

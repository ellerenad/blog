---
layout: post
title:  "The Fiasco Embedding Tweets in my Blog"
date:   2021-05-08T22:05:53+02:00
author: Enrique Llerena Dominguez
categories: miniblogging
tags: software_engineering problems solutions miniblogging
  
---

A couple of days ago, I was trying to embed a tweet to a blog post, but it was always failing to show the styles,
and it was driving me crazy as the task was rather easy: generate the code to embed the tweet, paste it on the blog, and we are ready to go.

After fiddling around, I found the problem was that I was testing in incognito mode in Firefox, which has [tracker protection](https://support.mozilla.org/en-US/kb/enhanced-tracking-protection-firefox-desktop),
which was blocking the request to download the required script from Twitter. The solution is of course not using incognito mode or
configure Firefox to make an exception. 

Below a screenshot of the problem:

<figure>
  <img src="/assets/miniposts/embedded-tweet-problem.png" alt="Showing the problem caused by Firefox tracker protection"/>
  <figcaption class="image-description">The Tweet was not properly shown because the tracker protection was blocking a call to Twitter</figcaption>
</figure>





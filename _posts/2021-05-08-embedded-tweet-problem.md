---
layout: post
title:  "The Fiasco Embedding Tweets in my Blog"
date:   2021-05-08T22:05:53+02:00
author: Enrique Llerena Dominguez
categories: miniblogging
tags: software-engineering problems solutions miniblogging
  
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


Send me a Tweet with your feedback!

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">A couple of days ago, I was trying to embed a tweet to a blog post, but it was always failing to show the styles. Why? Firefox was blocking a tracker -&gt; <a href="https://t.co/mjTYpI4KE0">https://t.co/mjTYpI4KE0</a><a href="https://twitter.com/hashtag/blog?src=hash&amp;ref_src=twsrc%5Etfw">#blog</a> <a href="https://twitter.com/hashtag/software?src=hash&amp;ref_src=twsrc%5Etfw">#software</a> <a href="https://twitter.com/hashtag/fun?src=hash&amp;ref_src=twsrc%5Etfw">#fun</a> <a href="https://twitter.com/hashtag/IEnjoySoftwareDev?src=hash&amp;ref_src=twsrc%5Etfw">#IEnjoySoftwareDev</a></p>&mdash; Enrique Llerena Dominguez (@ellerenad) <a href="https://twitter.com/ellerenad/status/1391141297168211970?ref_src=twsrc%5Etfw">May 8, 2021</a></blockquote> 


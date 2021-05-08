---
layout: post
title:  "Experiments in Agile Software Development Teams"
date:   2021-04-30T10:26:53+02:00
author: Enrique Llerena Dominguez
categories: methodologies
tags: software_engineering agile methodology
cover:  "/assets/posts/experimentation-agile/mick-haupt-eQ2Z9ay9Wws-unsplash.jpg"
cover_credits: Photo by <a href="https://unsplash.com/@rocinante_11?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Mick Haupt</a> on <a href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
  
---

# TL; DR

- Continuous improvement is in the agile manifesto [1]. Experimentation is a tool for continuous improvement.
- More often than not, this experimentation process lacks formality, confusing the teams on whether the experiment is successful or not.
- The author proposes to use the well-known scientific method in agile teams.
- The scientific method is described with an example of a common agile team pain.
- A template is added to make easier the application/adoption of the scientific method


# Continously improving

To continuously and iteratively improve a team or product is at the core of the agile methodology: either by delivering features that serve the needs of the customers or by changing processes that enable faster and better development of a codebase.

More often than not, we lack enough information to invest time in a change, not knowing whether this will be an improvement or a deterioration. On other occasions, we want to improve something which is already good or where the pains are not clear. For such situations, we can use experimentation.

# The Scientific method

There is enough information written about the scientific method, so I will not write details about it, but the main idea is: Based on an observation of a phenomenon or event, a hypothesis is formulated. Based on this hypothesis, predictions regarding the consequences are done. After that, using an experiment, these predictions are tested. Then, the data gathered in such an experiment is analyzed to see whether the predictions (and hence the hypothesis) are true or false.

<figure>
  <img src="/assets/posts/experimentation-agile/The_Scientific_Method.svg" alt="Describing the steps of the scientific method"/>
  <figcaption class="image-description">Describing the steps of the scientific method. Credits: By Efbrazil - Own work, CC BY-SA 4.0, https://commons.wikimedia.org/w/index.php?curid=102392470 </figcaption>
</figure>

From my perspective, one important aspect is that no matter whether a hypothesis is found to be “right” or “wrong” is a step forward: it is good to find how something is done and how it is not done.

# But what does this have to do with Agile and software engineering?

Let’s approach this with a story: a software engineer, Teresa, wants to improve a process: every day, the host of the 
next daily stand-up needs to be chosen.
But Teresa notices that this leads to a loss of time looking around for the next host.
So, after having gather data for a sprint, she raises this feeling on a retro and the team comes up with an action item: 
“For the duration of the next sprint, we keep a host for the whole week instead of rotating every day. 
This would make us more efficient, reducing the 1-2 minutes we need every day to find the next host.
Then, on the following retro, we evaluate whether this was a good solution or not”.

So, what do we have here?

<table>
    <tr>
        <td class="table-col-1"> Observation: </td>
        <td class="table-col-2">
             Loss of 1-2 minutes every day looking around for the next host.
        </td>
    </tr>
    <tr>
        <td class="table-col-1"> Hypothesis and prediction: </td>
        <td class="table-col-2">
              If we keep the same host for the daily stand up, then the team will stop spending 1-2 minutes per daily 4 
times per week. The fifth time per week, the next host needs to be selected.
        </td>
    </tr>
    <tr>
        <td class="table-col-1"> Experiment (including variables to measure): </td>
        <td class="table-col-2">
             For a week, the host is just selected once on Monday morning and they are responsible for the moderation of the daily stand-up.
             The following variables are measured: <br/>
             1. The time lost looking for a host.
        </td>
    </tr>
</table>


So, the sprint passes by, and the retro comes. It is time to evaluate the experiment and validate the hypothesis.

<table>
    <tr>
        <td class="table-col-1"> Analysis of the data: </td>
        <td class="table-col-2">
             Measured variables: <br/>
             1. 2 minutes on Monday. 0 minutes the rest of the week.
        </td>
    </tr>
    <tr>
        <td class="table-col-1">  Conclusion: </td>
        <td class="table-col-2">
             The hypothesis is correct. The measured variables behave as predicted: <br/>
             1. Looking for a host was reduced from 10 minutes per week before the experiment to 2 minutes per week during the experiment.
        </td>
    </tr>
</table>


This simple exercise of formalizing and documenting an arguably trivial user case transferred the agile team “from screwing around to doing science”



# Common sense

Of course, the above example is a rather trivial scenario. Doing this formalization and documentation effort is an overhead, so, as usual, it is about the trade-offs. My suggested rule of thumb is: if the experiment will take a considerable (where “considerable” is left to the criteria of the reader) amount of resources or its impact exceeds the short term or its consequences are hard to revert, do the effort and formalize it. This will also help other people trying to get the same knowledge. After all, that is how science is built upon.


# Suggested template

Remove the text in parenthesis.


<table >
    <tr>
        <td class="table-col-1"> Observation: </td>
        <td class="table-col-2">
            (Include a clear goal or pain, or even a question)
        </td>
    </tr>
    <tr>
        <td class="table-col-1"> Hypothesis and prediction: </td>
        <td class="table-col-2">
              (Include what you expect to happen after having taking an action. Make it specific, testable, and measurable.
This could also be seen as the goal of your experiment.)
        </td>
    </tr>
    <tr>
        <td class="table-col-1"> Experiment (including variables to measure): </td>
        <td class="table-col-2">
             (Define how you pretend to modify the variables based on the hypothesis and prediction)
        </td>
    </tr>
    <tr>
        <td class="table-col-1"> Analysis of the data: </td>
        <td class="table-col-2">
             (Gather the measurement of the variables of the experiment)
        </td>
    </tr>
    <tr>
        <td class="table-col-1"> Conclusion: </td>
        <td class="table-col-2">
            (Compare the measurements gathered on the experiment with the predictions done by the hypothesis. Prove the hypothesis true or false.)
        </td>
    </tr>
</table>

* Disclaimer: This is a common thing, adding this template here is just for facilitating purposes.


# Conclusion

Using a common scenario in an Agile team, the application of the scientific method was discussed:

1) An observation was made.<br/>
2) A hypothesis was formulated.<br/>
3) An experiment was designed and carried out.<br/>
4) Measurements were done.<br/>
5) The hypothesis was tested and considered to be true.<br/>

Also, a template with a small description of each step was added for facilitating purposes.

And, hey! “remember kids, the only difference between screwing around and science is writing it down” [2]

Send me a tweet with your feedback, I am eager to hear from you!

<style>
table, th, td {
  border: 1px solid #C0C0C0;
  padding: 1em;
}

.table-col-1 {
  width: 40%;
  font-weight: bold;  
}
</style>

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">We all like improving our processes and products by experimenting with them. But how can we be more effective? Have a look at my latest blog post :D <a href="https://t.co/BbDvV1fN64">https://t.co/BbDvV1fN64</a> <a href="https://twitter.com/hashtag/software?src=hash&amp;ref_src=twsrc%5Etfw">#software</a> <a href="https://twitter.com/hashtag/agile?src=hash&amp;ref_src=twsrc%5Etfw">#agile</a> <a href="https://twitter.com/hashtag/experiments?src=hash&amp;ref_src=twsrc%5Etfw">#experiments</a> <a href="https://twitter.com/hashtag/fun?src=hash&amp;ref_src=twsrc%5Etfw">#fun</a></p>&mdash; Enrique Llerena Dominguez (@ellerenad) <a href="https://twitter.com/ellerenad/status/1388238391653904384?ref_src=twsrc%5Etfw">April 30, 2021</a></blockquote> 
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

# References:

[1] Principles behind the Agile Manifesto, <https://agilemanifesto.org/principles.html>

[2] The origin of the "remember kids, the only difference between screwing around and science is writing it down", 
<a href="https://www.reddit.com/r/mythbusters/comments/3wgqgv/the_origin_of_the_remember_kids_the_only/" style="word-break: break-word;">https://www.reddit.com/r/mythbusters/comments/3wgqgv/the_origin_of_the_remember_kids_the_only/</a>



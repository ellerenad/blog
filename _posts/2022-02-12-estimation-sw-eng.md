---
layout: post
title:  "Breaking down the dimensions of estimation in Software Engineering"
date:   2022-02-12T19:25:52+01:00
author: Enrique Llerena Dominguez
categories: software-engineering
tags: software-engineering
cover:  "/assets/posts/estimation/adi-coco-kQW7xY7ponQ-unsplash.jpg"
cover_credits: Photo by <a href="https://unsplash.com/@adicoco?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Adi Coco</a> on <a href="https://unsplash.com/s/photos/roulette?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
  
---

Estimating software tasks is hard. There is a lot of literature on why, and how to approach it.

In this post, I want to show a simple way to break down problems the next time you estimate a task,
with a scrum focus. The output of this tool is story points, not hours.

We can break down the estimation in **four different dimensions**:
- **Complexity**: How hard is this to understand, both technically and from a domain point of view? How many components are involved?
- **Effort**: will the team need a high amount of time to complete it?
- **Uncertainty**: Are there unknowns? How well does the team know the code base, each other's skills, the technology, the business process?
- **Risk**: what external aspects endanger this task?

So, **the next time you need to do an estimation** or justify it in your team, you can say:

"My estimation is < X > story points, because I see a <high \| medium \| low> <Complexity \| Effort \| Uncertainty \| Risk>, because of..."

In my experience, **a task should have a maximum of one high aspect and one medium aspect**. If there are more, I suggest breaking down the task.

## One step further 

Developing this idea, you can even assign points like:
- High - 3
- Medium - 2
- Low - 1

So that a task can be estimated using the below table:

| Aspect      | Value  |   
|---|---|
| Complexity  |   |
| Effort      |   | 
| Uncertainty |   |
| Risk        |   |

This way, you can **quickly document** the logic behind the estimation in the ticket itself.


### Credits and acknowledgments

Thanks to Konstantin Briest ([LinkedIn](https://www.linkedin.com/in/konstantin-briest-hello-world/){:style="word-break: break-word;"}{:target="_blank"}),
who showed us the estimation dimensions in one the last projects I worked on :)  


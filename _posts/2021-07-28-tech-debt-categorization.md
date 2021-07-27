---
layout: post
title:  "Categorizing Technical Debt"
date:   2021-07-28T07:35:12+02:00
author: Enrique Llerena Dominguez
categories: software-engineering
tags: software-engineering 
cover:  "/assets/posts/tech-debt-categorization/jason-leung-SAYzxuS1O3M-unsplash.jpg"
cover_credits: Photo by <a href="https://unsplash.com/@ninjason?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Jason Leung</a> on <a href="https://unsplash.com/s/photos/money?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
---
# TL; DR

- A simple categorization of tech debt is proposed.
- With it, we win a common language that is understood by Product Owners or Project Managers and Software Engineers. A common framework stating clear
  consequences of tackling tech debt, so that it is easier to make decisions.
- Guidelines to estimate the risk and complexity of the tech debt items are provided.
- A basic payment strategy is presented.

A lot has been written about what technical debt is, e.g. Wikipedia[1] defines it like
"a concept in software development that reflects the implied cost of additional rework caused by choosing an easy solution now instead of using a better approach that would take longer.".

As in real life, debt is not always bad. When used wisely, debt can help you get long-term goods, like a car or a house,
and when used poorly, it can lead to a personal crisis. So, what is a wise use of the technical debt in software endeavors?

Breaking the components of debt (naively, if you want), we come up with a template to categorize technical debt:

- How much do you owe?
- Who do you owe?
- What are the consequences of not paying?

#### Example 1

- **How much do you owe?**
  - $1,000
- **Who do you owe?**
  - Your grandma
- **What are the consequences of not paying?**
  - Assuming your grandma knew the risks of giving money to her grandchild, your grandma would not get mad,
    but she'll be happy when you come by to visit her.

#### Example 2

- **How much do you owe?**
  - $100,000
- **Who do you owe?**
  - The bank
- **What are the consequences of not paying?**
  - The interests will be higher. After some months of not paying, they will come and repossess your house.

#### Example 3

- **How much do you owe?**
  - $100
- **Who do you owe?**
  - The Mafia. You thought it was gonna be an easy thing, right?
- **What are the consequences of not paying?**
  - Not surviving another day to pay it.


### Corollary
Even if the amount owed in the third example is 10x less than the first one, its consequences are bigger. My advice
here is: focus first on the items with higher consequences to effort ratio.

### Guidelines to calculate risk and complexity

To calculate the risk of a particular tech debt item, you can evaluate:
- How much more effort does the team require to develop new features because of this particular item?
- What is the impact on the value delivered to the customer?
- What is the impact of the application's performance?
- Is there a particular event soon that will make it much more hard fixing this? (e.g. a go-live)
- On the other hand, will this component be deprecated soon?
- Are there security implications? (e.g. dead API Endpoints not secured nor monitored, granting access to resources)
- How often does this cause trouble?

To calculate the complexity of "paying" an item, I recommend creating a ticket and refining it, so that the whole team can give their opinion. Consider:
- What are the implications of fixing it?
- What are the consequences on upstream and downstream flows?
- What is the level of uncertainty to fix it?


I will post another article on how to estimate complexity for all kinds of tasks ;)


### Payment Strategy

To prioritize the tech debt items, we can evaluate them in 2 axes:
* Complexity of paying the debt, AKA Amount of debt
* Risk of not paying

<figure>
  <img src="/assets/posts/tech-debt-categorization/tech-debt-categories.png" alt="Motorcycles and people detected by YOLO2"/>
  <figcaption class="image-description">Prioritizing tech debt.</figcaption>
</figure>


You can use the above graph as a rule of thumb, but not everything is easy to evaluate as high or low, there are 50 shades of grey.
The basic idea is that whatever is big needs to be broken down and categorized and depending on the risk, tackled ASAP or later.

### Examples with software products

#### Example 1

- **How much do you owe?**
  - 10 Story points aka Tech bucks (no cryptocurrency reference here :) )
- **Who do you owe?**
  - Feature Y was migrated to another component but was not cleaned up from the component X
- **What are the consequences of not paying?**
  - Increased maintenance/refactoring effort.
  - Risk of death code kicking in.
- **Payment strategy**
  - Since the death code is not relevant anymore, this is a low priority. Can be tackled in a future sprint.

#### Example 2

- **How much do you owe?**
  - 80 Story points
- **Who do you owe?**
  - Component Z has been around for 7 years, accumulating too much logic, developing spaghetti code.
- **What are the consequences of not paying?**
  - Increased maintenance/refactoring effort.
  - An increased effort of adding new features.
  - Too many people are required to do changes to it.
- **Payment strategy**
  - Long time effort.
  - Make a first down payment configuring another application to slice out functionality.
  - Pay slowly every sprint by slicing out functionality.


#### Example 3
- **How much do you owe?**
  - 1 Story point
- **Who do you owe?**
  - Component X, which is public on the internet, has an endpoint that allows changing the password of another user.
- **What are the consequences of not paying?**
  - User accounts getting hijacked.
  - Legal problems.
  - Reputation damage.
- **Payment strategy**
  - Fix it now, deploying a hotfix if possible.


# Conclusion
- A simple categorization was proposed so that both technical and non-technical people have a similar understanding of the consequences
  of the technical debt
- Such categorization is based on 3 questions:
  - How much do you owe?
  - Whom do you owe?
  - What are the consequences of not paying?
- Furthermore, guidelines to estimate the risk and complexity were provided, as well as a basic payment strategy.


### References
[1] Technical debt, Wikipedia, https://en.wikipedia.org/wiki/Technical_debt. Retrieved 05/2021

---
layout: post
title:  "Learning in public:  Google Dialogflow"
date:   2021-08-12T01:10:12+02:00
author: Enrique Llerena Dominguez
categories: software-engineering
tags: software-engineering 
---

# TL;DR
- The basic concepts of the Google Dialogflow are shown
- A basic agent is created to retrieve facts about Chuck Norris 
- This is a work in progress
- resources can be found at <a href="https://cloud.google.com/dialogflow/" target="_blank">https://cloud.google.com/dialogflow/</a>

# What is *my* concept of learning in public?

My idea is to add here the notes that I take when studying something, maybe they are useful for someone else :)
This is not intended as a tutorial or a step by step guide.
I take notes manually and then transcript them here. This way I can review them and save them for the posterity :)
Please bear with my syntax/style errors :)

# Basic concepts

### What is Dialogflow?
- Google provides the definition of "Dialogflow is a natural language understanding platform that makes it easy to design and integrate a conversational user interface into your mobile app, web application, device, bot, interactive voice response system, and so on. Using Dialogflow, you can provide new and engaging ways for users to interact with your product."
- I understand it like a platform with tools to design a voice user interface (in contrast to a graphic user interface) to other computational resources.
- It is also possible to model dialogs with static data or just using the same information that the user "inputs".


### Main entities

#### Agents
- Natural Language (NL) understanding module
- Parses the voice input to structured data required by the app/API behind the user interface (UI)
- It is configured by the developer
- Analogy to GUI: the role is like a page where you define a form, but with natural language processing "magic" to transform the data instead of the user typing it.

#### Intents
- This represents what the user wants to do.
- Consists of:
  - Training phrases: 
    - Example phrases that match this intent
    - "trigger" for this intent
  - Action:
    - What should be done if this intent is matched. E.G. return a predefined answer, call a webhook, execute a cloud function 
  - Parameters
    - Information obtained from the input of the user
    - This is structured data parsed by the agent (see "Entities" below), that can be used in other computational systems
  - Responses
    - What the agent will return to the user. It could be text, audio, images,...
- Analogy to GUI: The web form itself, along with the action it triggers, and the response it gets
  
#### Entities
- Types of parameters
- Form of the data
- I understand it like a class (in an object oriented context)
- There are predefined entities (and even in the editor, sometimes they are detected automatically, which is cool)
- Able to define you entities

#### Contexts
- The information surrounding the conversation, just like a regular talk with a person
- helps to understand what the user means
- An intent can be configured using input and output contexts

#### Follow-up intents
- can be used to automatically set contexts for pairs of intents
- child-parent relationship with another intent

#### Dialogflow console
- console to create, build and test agents

#### Dialogflow api
- build agents for advanced scenarios

#### Integrations
- existing integrations with other services, e.g. telegram, fb messenger

#### Fulfillment for integrations
- Possibility to call APIs owned by the developer to get information to respond to the user
- Configured for the required intents

#### User interactions with the API
- Control is inverted, i.e. your code interacts with the user and then sends the input (text or audio) to the dialogflow
api to retrieve the intent
  
### Interesting things/features
- API to create and manage agents
  - I find this one important because it allows to have the agents as code, which enables change traceability and stateless deployments
  - No one wants to have manually tweaked agents deployed to production -> that is unreliable
- Fulfillment
  - different ways to configure authentication against your service
  - 2 ways to do the fulfillment:
    - webhook with defined interface
    - execution of cloud functions (think of lambda) to process data (e.g. call a backend)
  - on the docs, it is recommended to use the webhook for production, which I don't fully understand yet: calling a cloud function should be reliable enough
- Example code to execute the cloud function is understandable, I was able to edit it and get it working in minutes (even after midnight 🙈)  

### Problems that I found and things that I am missing or probably not found yet
- I miss a webhook editor for fulfillment
  - The current webhook is way too rigid, an editor could make the tool more friendly for people with no code experience
- On the console, the option to enable the fulfillment is confusing: you need to enable fulfillment by webhook to use the cloud function,
whereas on the fulfillment editor, webhook and cloud function are mutually exclusive
- I wonder:
  - whether it is easy to test agents this using code / the API
  - how to "debug" agents (why is one intent recognized instead of the other?) 
  - how can I deploy the agent? e.g. use it in my mobile or in a smart home device? are there test environments?

# Hands on! Creating a basic agent




# Conclusion
- Dialogflow is an interesting tool allowing to create agents in minutes.
- I just had a quick grasp on the surface to get to know it.
- There are some unknowns on my side about testing. Maybe I just need to dive deeper :)

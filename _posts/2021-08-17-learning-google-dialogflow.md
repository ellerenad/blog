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

# What is *my* concept of learning in public?

My idea is to add here the notes that I take when studying something, maybe they are useful for someone else :)
This is not intended as a tutorial or a step by step guide

# Basic concepts

### What is Dialogflow?
- Google provides the definition of "Dialogflow is a natural language understanding platform that makes it easy to design and integrate a conversational user interface into your mobile app, web application, device, bot, interactive voice response system, and so on. Using Dialogflow, you can provide new and engaging ways for users to interact with your product."
- I understand it like a platform with tools to design a voice user interface (in contrast to a graphic user interface) to other computational resources.

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

#### Follow-up contexts

TBD...




# Hands on! Creating a basic agent


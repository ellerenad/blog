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
- A PoC basic agent is created to retrieve facts about Chuck Norris 
- This is a work in progress
- Resources can be found at <a href="https://cloud.google.com/dialogflow/" target="_blank">https://cloud.google.com/dialogflow/</a>

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
- There are predefined entities (and even in the Dialogflow console sometimes they are detected automatically out of the training phrases, which is cool)
- Possibility to define you entities

#### Contexts
- The information surrounding the conversation, just like a regular talk with a person
- Helps the agent to understand what the user means
- An intent can be configured using input and output contexts

#### Follow-up intents
- Can be used to automatically set contexts for pairs of intents
- Child-parent relationship with another intent

#### Dialogflow console
- Console to create, build and test agents

#### Dialogflow api
- Build agents for advanced scenarios
- From my perspective, this is a basic feature for production use cases. 
- Could it be that I am mixing concepts here? need to dig deeper. Is this API a substitute of the dialogflow console to model agents?
Is this API to get an intent out of the natural language input by the user? is it both?

#### Integrations
- Existing integrations with other services, e.g. telegram, fb messenger

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
  - This also enables version control of agents
- Fulfillment
  - Different ways to configure authentication against your service
  - 2 ways to do the fulfillment:
    - Webhook with defined interface
    - execution of cloud functions (think of lambda) to process data (e.g. call a backend)
  - Logs of the cloud function are accessible in one click, though sometimes they take long load
  - On the docs, it is recommended to use the webhook for production, which I don't fully understand yet: calling a cloud function should be reliable enough
  - Example code in Node.js to execute the cloud function is understandable, I was able to edit it and get it working in minutes (even after midnight 🙈),
though there could be a comment on what is required to make the agent return a response, it took me a couple of minutes to decipher it.

### Problems that I found and things that I am missing or probably not found yet
- I miss a webhook editor for fulfillment
  - The current webhook is way too rigid, an editor could make the tool more friendly for people with no code experience
- On the console, the option to enable the fulfillment is confusing: you need to enable fulfillment by webhook to use the cloud function,
whereas on the fulfillment editor, webhook and cloud function are mutually exclusive
- I wonder:
  - Whether it is easy to test agents using code / the API
  - How to "debug" agents (why is one intent recognized instead of the other?) 
  - How can I deploy the agent? e.g. use it in my mobile or in a smart home device? are there test environments?
  - To perform automated tests: can I create and destroy agents on demand? can I specify what agent I want to call?
  

# Hands on! Creating a basic agent - PoC

I want to create an agent that delivers random facts about Chuck Norris. 

The API I will use is at [https://rapidapi.com/matchilling/api/chuck-norris/](https://rapidapi.com/matchilling/api/chuck-norris/){:target="_blank"}, and
it is free, you just need to signup. It also provides nice code snippets to perform the call, even in node.js ;)

On the first iteration, there is just a single intent to retrieve a random fact.

On a high level, the idea is:
- Get the rights to call the required API
- Create an agent
- Create an intent
  - Add training phrases like "tell me a random fact about chuck norris", "tell me a fact about chuck norris"  
  - On the fulfillment editor, enable the 
  - Enable the fulfillment -> "Enable webhook call for this intent" (which is confusing because I want to use a cloud function, but whatever 🤷‍)
  - Add the required code to the cloud function.

Regarding the required code on the cloud function, the idea is:
- Map the intent to a function handler
- In such function handler, call the Chuck Norris facts API
- Add the library Axios to the package.json
So, the most important parts of the code end up looking like: 

- Map the intent to a function handler
```javascript
 // Run the proper function handler based on the matched Dialogflow intent name
  let intentMap = new Map();
  intentMap.set('random fact', chuckNorrisFact); // 'random fact' is the intent's name 
  agent.handleRequest(intentMap);
```

- In such function handler, call the Chuck Norris facts API. 
  - Important to use async/await, otherwise the agent does not show the result of the API call to the user. There might be better ways to do this like with promises, but for this PoC this is ok.

```javascript
 async function chuckNorrisFact(agent){
    console.log("chucknorrisFact: entered function");
    var axios = require("axios").default;

    var options = {
      method: 'GET',
      url: 'https://matchilling-chuck-norris-jokes-v1.p.rapidapi.com/jokes/random',
      headers: {
        accept: 'application/json',
        'x-rapidapi-key': '<your api key>',
        'x-rapidapi-host': 'matchilling-chuck-norris-jokes-v1.p.rapidapi.com'
      }
    };
	  console.log("chucknorrisFact: about to perform the API call");
    await axios.request(options).then(function (response) {
      console.log("chucknorrisFact: got a response from the fact call");  
      console.log(response.data);
      // This does the magic of having the agent return the data to the user  
      agent.add('Sure! how about: ' + response.data.value);
    }).catch(function (error) {
        console.error('chucknorrisfact: Error: ', error);
    });
    console.log("chucknorrisFact: leaving function");
  }
```

And here you see the test!  🚀🚀🚀

<figure>
  <img src="/assets/posts/learning-google-dialogflow/test_chuck_norris_facts.png" alt="Testing the ChuckNorrisFacts Dialogflow Agent"/>
  <figcaption class="image-description">Testing the ChuckNorrisFacts Dialogflow Agent</figcaption>
</figure>


A detailed step-by-step guide is not provided because it is out of the scope of ths post, but you can find the steps plus much more at [https://cloud.google.com/dialogflow/es/docs/quick](https://cloud.google.com/dialogflow/es/docs/quick){:target="_blank"}

## Next iteration

The ChuckNorrisAPI provides a fact search function, so an intent could be created to search by a specific theme input by the user. This could
exercise how to extract parameters from the users' natural language input.

# Conclusion
- Dialogflow is an interesting tool allowing to create agents in minutes.
- The concepts are easy to understand, even more if you have an understanding of other kind of user interfaces, like graphical user interfaces.
- The processing of converting natural language input into structured data is properly encapsulated - which has its own disadvantages, e.g. debug-ability  
- I just had a quick grasp on the surface to get to know it.
- There are some unknowns on my side about testing. Maybe I just need to dive deeper :)

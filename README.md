# CORONA-FAQ-CHATBOT-USING-RASA-NLU

## Main Objective :
The goal here is to build a chatbot which can answer queries related to the COVID-19 disease.
## Introduction:
There are viral rumors  about corona epidemic over the internet and social media which panicked the common people.So this chatbot was designed to answer all the queries regarding Corona Virus Disease 19
FAQs and answers are prepared based on Information collected from authorized sources: CDC,WHO..etc
## What is a chatbot??
A chatbot is a computer application that can initiate a conversation as well as it can respond to queries as the humans would do.
## Types of chatbots:
#### 1.	A simple rule-based engine
•	simple if else construct
•	easy to build
•	not very user friendly(only for technical people)
•	dependencies depend on the developer’s skill

#### 2.	An intelligent application leveraging Natural Language Understanding
•	Very common
•	Used by end users
•	Have Natural Language understanding Engine
•	Can understand customer intention(NLU) and responds accordingly(NLG-Generation)

## Advantages of chatbots:
•	High Availability-available 24*7
•	Easy to build
•	Cost Effective
•	Provides uniform customer experience
•	Wide application 


## Uses of chatbots:
•	Customer support
•	Frequently Asked Questions
•	Addressing Grievances
•	Appointment Booking
•	Automation of routine tasks
•	Address a query

## Prerequisites
       For developing and understanding a chatbot we need 
•	Python installed
•	Microsoft Build tools with visual c++ 14.0  and Visual Studio installed as windows has dependency on these

## RASA
Rasa is an open source machine learning framework for building contextual AI assistants and high performing chatbots. Rasa employs machine learning and deep learning in background to improve conversation experience

     Rasa has two main modules:
•	NLU for understanding user messages 
•	Core for holding conversations and deciding what to do next 

Rasax is a free, closed source tool available to all developers. It is  the layers on top of Rasa Open Source and provides

•	a Graphical User Interphase to test our chatbots
•	Enables review of conversations and a better assistant
•	Improves system based learning
•	We can select the model  for conversation(old  or pre-trained model)
•	Easily deploy new updates
•	Can be deployed anywhere and training data stays secured and proprietary 

## RASA Architecture
 
 ![image](https://user-images.githubusercontent.com/71456028/110434396-315fa400-80cb-11eb-8812-01ab9ed4b5f2.png)


Message in: What the user says
Interpreter: User’s message is its input and it extracts the intents and entities out of the message 
Tracker: Holds current state of the conversation(latest kind of conversation is happening)
Policy : what action to taken after analyzing the current state of the chatbot
Action : Based on old state what new action has been taken is updated to the tracker
Message out : Final message sent out to the user

## Application Flow:
![image](https://user-images.githubusercontent.com/71456028/110434545-64099c80-80cb-11eb-8a2a-0e7800496063.png)

## WorkFlow:

1.	Open the chatbot project folder using Pycharm
2.	Create a new environment for your chatbot project from pycharm or from anaconda prompt.
3.	pip install rasa
4.	Run the command pip install rasa x for installing all the rasa dependencies
•	This is to visualize our conversations
5.	Run the command pip install spacy for installing spacy library.
•	Rasa internally use spaCy for text processing
•	spaCy is an open-source software library for advanced natural language processing, written in the programming languages Python and Cython
•	 provides software for production usage. 
•	spaCy also supports deep learning workflows that allow connecting statistical models trained by popular machine learning libraries like TensorFlow, PyTorch or MXNet through its own machine learning library Thinc
#### 	Main Features of SpaCy
•	Non-destructive tokenization
•	Built-in support for trainable pipeline components such as Named entity recognition, Part-of-speech tagging, dependency parsing, Text classification, Entity Linking and more
•	Statistical models for 17 languages
•	Multi-task learning with pretrained transformers like BERT
•	Support for custom models in PyTorch, TensorFlow and other frameworks
•	State-of-the-art speed and accuracy
•	Production-ready training system
•	Built-in visualizers for syntax and named entities
•	Easy model packaging, deployment and workflow management
6.	Then enter the following  3 commands:
i.	python -m spacy download en  
[Downloading English libraryfrom spacy]

ii.	python -m spacy download en_core_web_md
[Another library in spacy for text preprocessing]

iii.	python -m spacy link en_core_web_md en

7.	After all this command run successfully, enter the command rasa init and for all the subsequent actions choose Y (Yes-for training the model etc).
•	Rasa init will initialize the rasa context
•	This will create the folder structure required for us to build a chatbot

8.You’ll then end up with all the predefined structures which RASA would have built automatically, as shown below:
![image](https://user-images.githubusercontent.com/71456028/110434767-a8953800-80cb-11eb-8bba-2c2357591888.png)

9. Open the ‘nlu.md’ file from the data folder and enter the following content:
•	This file is used to create all the intents and their sample utterances for conversation.
•	These are all intents from user side
## intent:greet
- hey
- hello
- hi
- good morning
- good evening
- hey there

## intent:goodbye
- bye
- goodbye
- see you around
- see you later

## intent:bot_challenge
- are you a bot?
- are you a human?
- am I talking to a bot?
- am I talking to a human?

## intent:corona_intro
- What is corona virus
- what is covid
- what is a novel corona virus
- what is covid-19
- tell me about corona
- can you tell me about covid

## intent:corona_spread
- how does corona virus spread
- how does the virus spread

## intent:corona_food_spread
- Does corona spread from food
- how will corona spread from food

## intent:warm_weather
- will warm weather stop the spread
- will it stop with warm weather

## intent: high_risk
- who is at a higher risk of infection

9.  Open the ‘domain.yml’ file and put the following content:
•	These are the responses of chatbot
       
  session_config:
  session_expiration_time: 60
  carry_over_slots_to_new_session: true
## intents:
- greet
- goodbye
- bot_challenge
- corona_intro
- corona_spread
- corona_food_spread
- warm_weather
- high_risk
## responses:
  utter_greet:
  - text: Hey! How are you?
  utter_did_that_help:
  - text: Did that help you?
  utter_goodbye:
  - text: Bye
  utter_iamabot:
  - text: I am a bot, powered by Rasa.
  utter_corona_intro:
  - text: Coronaviruses are a group of related viruses that cause diseases in mammals
      and birds. In humans, coronaviruses cause respiratory tract infections that
      can be mild, such as some cases of the common cold (among other possible causes,
      predominantly rhinoviruses), and others that can be lethal, such as SARS, MERS,
      and COVID-19
  utter_corona_spread:
  - text: "This virus was first detected in Wuhan City, Hubei Province, China. The\
      \ first infections were linked to a live animal market, but the virus is now\
      \ spreading from person-to-person. It’s important to note that person-to-person\
      \ spread can happen on a continuum. Some viruses are highly contagious (like\
      \ measles), while other viruses are less so. The virus that causes COVID-19\
      \ is spreading from person-to-person. Someone who is actively sick with COVID-19\
      \ can spread the illness to others. That is why we recommend that these patients\
      \ be isolated either in the hospital or at home (depending on how sick they\
      \ are) until they are better and no longer pose a risk of infecting others.\n\
      How long someone is actively sick can vary so the decision on when to release\
      \ someone from isolation is made on a case-by-case basis in consultation with\
      \ doctors, infection prevention and control experts, and public health officials\
      \ and involves considering specifics of each situation including disease severity,\
      \ illness signs and symptoms, and results of laboratory testing for that patient.\n\
      The virus that causes COVID-19 seems to be spreading easily and sustainably\
      \ in the community (“community spread”) in some affected geographic areas. Community\
      \ spread means people have been infected with the virus in an area, including\
      \ some who are not sure how or where they became infected."
  utter_corona_food_spread:
  - text: Coronaviruses are generally thought to be spread from person-to-person through
      respiratory droplets. Currently there is no evidence to support transmission
      of COVID-19 associated with food. Before preparing or eating food it is important
      to always wash your hands with soap and water for 20 seconds for general food
      safety. Throughout the day wash your hands after blowing your nose, coughing
      or sneezing, or going to the bathroom.
  utter_warm_weather:
  - text: It is not yet known whether weather and temperature impact the spread of
      COVID-19. Some other viruses, like the common cold and flu, spread more during
      cold weather months but that does not mean it is impossible to become sick with
      these viruses during other months.  At this time, it is not known whether the
      spread of COVID-19 will decrease when weather becomes warmer.  There is much
      more to learn about the transmissibility, severity, and other features associated
      with COVID-19 and investigations are ongoing.
  utter_high_risk:
  - text: Older adults and people of any age who have serious underlying medical conditions
      may be at higher risk for more serious complications from COVID-19. These people
      who may be at higher risk of getting very sick from this illness, includes;
      Older adults, People who have serious underlying medical conditions like...
      Heart disease, Diabetes, Lung disease,
actions:
- utter_greet
- utter_did_that_help
- utter_goodbye
- utter_iamabot
- utter_corona_intro
-utter_corona_spread
- utter_corona_food_spread
- utter_warm_weather
- utter_high_risk

10. Open the ‘stories.md’ file from the data folder and put the following content:
•	The order of conersations id defined in stories.md(what and when to say )
## say goodbye
* goodbye
  - utter_goodbye

## bot challenge
* bot_challenge
  - utter_iamabot

## what is corona
* corona_intro
  - utter_corona_intro

## how does corona spread
* corona_spread
  - utter_corona_spread
## corona food spread
* corona_food_spread
  - utter_corona_food_spread

## corona warm weather
* warm_weather
  - utter_warm_weather
## corona high risk
* high_risk
   - utter_high_risk

•	This file is used to create the conversation flows.
•	After all this, enter the command ‘rasa train’ to train the model with new conversation elements.
After the training is completed, enter the command ‘rasa x’ to test your chatbot in the web UI. You’ll see

2021-03-03 17:58:28 INFO     root  - Starting Rasa server on http://localhost:5005
2021-03-03 17:58:37 INFO     root  - Rasa server is up and running.


11.Type rasa shell
12.Now start chating with the bot

13.Now the chatbot is running locally. For anyone access it we need to integrate it in a common platform. Here lets use telegram

1.	Telegram Integration:
•	Download ngrok from https://ngrok.com/download
•	After extracting the zip file, open the ngrok file and run it.
•	In ngrok, enter the command ‘ngrok http 5005 ’:
•	 
•	Now what happens is localhost:5005 address is masked by a new https url  :  https://698708a24d04.ngrok.io
•	This will create a public HTTPS url for your locally running Rasa X server, given that it is running at the default port 
•	So that anyone can access it
 

•	Then go to telegram and create your own bot using Botfather:
a)	Open the telegram app and search for botfather(it is an inbuilt bot used to create other bots)
b)	Start a conversation with botfather and enter /newbot to create a newbot.
c)	Give a name to your bot -coro_bot_19
d)	Give a username to your bot, which must end in _bot.This generates an access token. – coro_19_bot

•	Open ‘credentials.yml’ and enter:
telegram:
access_token: "obtained from telegram"
verify: "your bot username"
webhook_url: https://<ngrokurl>/webhooks/telegram/webhook

 ![image](https://user-images.githubusercontent.com/71456028/110435275-47219900-80cc-11eb-9bf5-53cd237c82df.png)

•	Now what happens is localhost:5005 address is masked by a new https url  :  https://698708a24d04.ngrok.io
•	This will create a public HTTPS url for your locally running Rasa X server, given that it is running at the default port 
•	So that anyone can access it

![image](https://user-images.githubusercontent.com/71456028/110435458-7c2deb80-80cc-11eb-8d43-438f16c2563d.png)

•	Go to terminal and enter the command ‘rasa run’
•	Open one more terminal and run the command ‘rasa run actions’
◦	This starts action terminal in the background and we get
◦	Action endpoint is up and running on http://localhost:5055
◦	Rasa is running on port 5005 that’s why in ngrok window port number is given as 5005
•	Now, you can chat with your bot from Telegram.

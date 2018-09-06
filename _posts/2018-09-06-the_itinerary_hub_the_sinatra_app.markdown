---
layout: post
title:      "The Itinerary Hub: The Sinatra App"
date:       2018-09-06 22:11:21 +0000
permalink:  the_itinerary_hub_the_sinatra_app
---


When I started to brainstorm ideas for this project, I wanted to do something that showcased another interest of mine. I decided to incorporate my interest of history and traveling for the Sinatra App where users could build an itinerary of destinations. It's been a very long road to get here, but I'm continuing the journey. I had less anxiety surrounding this project since I became more comfortable with the activerecord, sinatra and SQL concepts a lot quicker than CLI.  

After reading through the requirements, I began to plan out the data structure for the app. First, I created the Gemfile, the Rakefile, and the Environment file that way I could avoid most of the syntax errors I might have encountered later on. From there, I created the migrations for both a user and a itinerary. It was important that a user not only had the ability to sign up, but could also have a unique username and password. An Itinerary would include destinations, travel_guide, and schedule that a user could personalize on their own. All of the information would be stored and organized under one itinerary. 

Launching the models and created a rough sketch of the controllers and views was the next step. In the User model, I included that a user has secure_password and has_many relationship with itineraries. This gives the user the ability to create multiple itineraries for their upcoming trips. In the Itinerary model, the belongs_to user relationship was coded. Also, I made sure that all of the components (destinations, travel guide, and schedule) of the itinerary were validated. 

Once the migrations and models were finished, I started to build out the users controller, which took longer than I anticipated. I had remembered learning about "yield" in the Sinatra unit, but was confused on where to place it in the index or layout page of the app. So while I had the get and post 'signup' and 'login' methods built out, I kept running into errors constantly. I spent hours scrolling through each of the methods to see if I had some minor errors, but every line of code was efficient. It wasn't until I reached to a technical coach where I realized that the issue was "yield." From there, I figured it was not only important to test each file, but to make sure it looked organized once running shotgun. I decided to include a slugifiable to keep more structured. This helped significantly as now each user would be assigned a specfic slug without having to click the back arrows to access an itinerary.

After finishing the users controller, I moved onto the itineraries controller, which was a bit more problematic. Not only did I want users to create an itinerary, but creating the methods for the edit and delete functions took days. I wanted to solve the issue on my own and what it came down to was an extra 'end' and one of the lines being an instance instead of an instance variable. It's really simple mistakes like these that kept me frustrated throughout this process, but I worked through the struggles successfully. Interestingly enough, I though most of the errors would initiate from params, so that also made the project less overwhelming. I'm hoping that when I reach the Rails project, I will have more confidence and better time management skills. 

Overall, through the app, users can create an account and begin creating their own itineraries from their index page. When the users logs in, they will be provided with a welcome message and their current itineraries will be printed. Even though, users aren't able to edit and delete other users itineraries, they are still allowed to view them in the app's index. This gives them the option to eventually connect with other users and share their upcoming travel experiences. 



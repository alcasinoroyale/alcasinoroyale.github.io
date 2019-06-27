---
layout: post
title:      "Rails with JS Project: Expanding Renecades"
date:       2019-06-27 15:33:19 -0400
permalink:  rails_with_js_project_expanding_renecades
---

One of the greatest challenges going into this project was creating and testing all of the JS functions to expand Renecades. My only experience with Javascript before joining the Flatiron was when I was a Journalism student, but it was more a novice level.  Going into this unit, I didn't expect the many obstacles I would unravel, particularly because a lot of the labs that I forked and cloned from GitHub didn't always function properly. Different versions of gems and trouble with the compatibility of IDE and Atom made it more difficult. It was quite a long journey to get to this point, but I think once I took advantage of Flatiron's resources more, I learned a great deal about myself and my ability to code. 

While I do think the labs and lessons prepared me, I will admit that my comfort level with JS wasn't as strong as it's a lot more expansive than Ruby on Rails. During the first few days working on the project, I planned out which functions and methods would meet the requirements and looked back through my notes to find anything necessary that would help. It was really a huge test of my knowledge because I spent weeks experimenting with Javascript along with this project. And while it was a stressful experience, it was a lot easier for me to comprehend how the console reflected the games.js file. 

First I started building out all of the functions that will be accessible and displayed throughout the app. This includes createGame, loadGames, and nextGame, all of which add an exclusive feature from JS on top of the Rails application. Since Renecades has more than one has_many through relationship, this is where a lot of the time was lost. The nested routes became an even bigger issue because it would give me constant errors that the app goes a level too deep. In the end, I had to streamline the features that I wanted to add particularly for categories and reviews. I set a strong focus on the games pages because that's where the user interacts the most with the app. 

![](https://i.imgur.com/ycgooTf.png)

In the createGame function, after a user accesses the form for a new game and fills in the game info, the submit button will launch and create a new object through JS. I did a lot of testing figuring out what would work best and decided to use an ajax request. This lets the server and browser know the location of where the data will be appended to. All of the attributes that I provided in the game object constructor will be serialized and appended to the DOM with a new ID, but the display will depend on the prototype for a newGame form.  Before accessing the index page, the information that they inserted into the textboxes will dynamically render and once they navigate to the index, it will provide the user with a message stating that the game has been created successfully. 

Since I have the index and create actions respond to both the html and json format, we can also view the json data to make sure everything is working properly. In order to load the list of games in the index, I used the history.pushState method and then fetched the list of games from the json data and eventually appended the list with the gameHtml variable to the renecades container that I have in the application layout. It was able to append each game in the list not only because of the forEach method, but because of the constructor and prototype in order to have the attributes. 

![](https://i.imgur.com/EFQY7sN.png)

Depending on the data that's posted, it will change the ordered list of games. For each game on the index page that a user clicks on, it will provide some basic info about the game including the description and reward points. If they want to view more details, they can click on the game link and it will navigate to the new URL for that specific game. Once I was able to successfully implement the prototype for Game, everything worked a lot more efficiently. Even though my comfort level with Javascript significantly improve throughout this project, there is always more to digest and expand on moving forward. 

Another feature added to the show page was the next game button where a user can jump to the next game in the list without having to change the URL. In the games.js file, I built the function using parseInt and increment by 1 to return the next game in the iterated list based on the ID. It will then append to the DOM and display the attributes that are provided in the formatShow prototype object for a game. I used the join method in order to add current players if there are any, otherwise, that part won't render on the page.

One of the biggest takeaways from the project was patience. Experimenting and testing your code can be a time-consuming process, but it's also where you absorb the most valuable information. It was good to have the Javascript guides a reference because the vocabulary is endless. It's important to stay organized and remember that debugging can often take the longest, but the task becomes less daunting with more practice. The code could look amazing from a visual perspective, but refactoring is an instrumental component in becoming a successful programmer. 


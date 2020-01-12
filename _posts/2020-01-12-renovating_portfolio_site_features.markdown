---
layout: post
title:      "Renovating Portfolio Site Features"
date:       2020-01-12 20:43:49 +0000
permalink:  renovating_portfolio_site_features
---


In my previous blog post, I described some of my experience developing my portfolio site using the React framework such as building the navigation, designing the layout, and providing functionality for all of the components. While the site works sufficiently on a desktop, viewing my portfolio on a tablet or mobile device is not responsive. All of the components have unusual padding and margin properties that allow for convenient navigation. I think it would be a great idea to not only explain this process, but also share some of the other features that I want to renovate for this month. Besides the lack of a responsive menu and jumbled content containers when reducing the screen size, another problem I've encountered is the page refresh for the portfolio and contact pages. 

When you access the site with portfolio or contact in the domain after the home page URL, it will display a 404 "file not found" error with the message "the site configured at this address does not contain the request file." Having deployed my portfolio site using gh-pages, I wasn't sure how to solve this, but I've done some research and found a potential answer. One strategy would be to call a reload method and build a function that allows a refresh of the window using a button onClick before deploying the application. Another would be to update the state of the component based on the rendering activity instead of relying on a reload function. Both of these are certainly manageable, but updating the state would be a more secure practice. 

For the social media and skills icons, I've mostly implemented the font awesome package for them to display, but also scaled down the size so that they could be structured in columns. As I continue to expand my resume and skillset, the layout would have to change because the text under the icons would continue to overlap. Besides creating a responsive menu for the navigation, using a media screen function in the profile's CSS file could help to organize the icons. Instead of the icons being aligned close together, they could be stacked in a vertical column or even hidden inside of a container that would be clickable if the user wanted to see a showcase of the portfolio skills.

In terms of the portfolio projects, since I've modified a handful of features for all three of them since the curriculum, it would be awesome to showcase those updates through a restructure of the content containers. Currently, the content and visuals of the Itinerary Hub, Reel 2 Reel, and Reneacdes Gameroom resemble the initial GitHub and curriculum submissions so the new layout would include updated images and demos of the user interface as well as more detailed summary of what each application does.  Another component would be to deploy the applications to a cloud platform such as Heroku so that users and employers can see everything that I've changed in a live setting. 

Finally, the contact page lacks a message form. In my original plan, I had an idea of building a form where users could fill out their info and send a message to my email, but because this involved a restructure and downloading packages that I wasn't familar with, I delayed this feature to focus on finishing the rest of the pages. Now having learned some other JS frameworks such as Angular, I'm not as hesistant to understand the process. I wanted to take on the challenge of building a portfolio using a framework instead of wordpress or squarespace templates. One of the goals for this week is to do some more research on how to connect my email to the portfolio site without a large amount of code.



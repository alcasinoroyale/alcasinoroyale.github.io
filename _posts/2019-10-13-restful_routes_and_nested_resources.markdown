---
layout: post
title:      "Restful Routes and Nested Resources"
date:       2019-10-13 21:11:31 +0000
permalink:  restful_routes_and_nested_resources
---

Having spent the past few months building in React, I wanted to travel back to my Ruby on Rails applications to modify and add features that I had sketches for, but never implemented. I think that it's important to continue building and innovating your earlier projects as you gain a greater understanding of each programming language and their functionality. It was interesting to explore Restful Routes and Nested Resources, something that I had overcomplicated myself with while originally creating Renecades Gameroom. 

Starting with the restful routes, they are incredibly significant to the functionality of Ruby on Rails applications. They provide the architectural mapping between HTTP verbs and CRUD actions. CRUD refers to Create, Read, Update, and Delete while the HTTP verbs are get, post, patch, put, and delete. This can become confusing when you're working across multiple files within your application. 

If you type "rake routes" in the terminal, it will provide you with a list of routes that are defined in app/config/routes.rb. This will display the prefix, verb, URI pattern, and the controller action for each resource. 

Let's say you only wanted to focus on one resource. For example "games", if you type "rake routes -c games" since the controller handles the user requests, it will now provide the routes that correspond to that specific controller.

| Prefix | Verb | URI Pattern | Controller#Action |
| -------- | -------- | -------- | -------- |
| games | GET | /games | games#index |
| games | POST  | /games  | games#create |
| new_game | GET | /games/new | games#new |
| edit_game | GET | /games/:id/edit | games#edit |
| game | GET | /games/:id | games#show |
| game | PATCH | /games/:id | games#update |
| game | PUT | /games/:id | games#update |
| game | DELETE | /games/:id | games#destroy |

In my games show view, I have a link to edit the game if you are the creator and edit_game_path(@game) will redirect to the edit form for that specific game. GET is the HTTP verb because it retrieves the data from the form enabling us to start editing the attributes.

```
<%= link_to "Edit Game", edit_game_path(@game) if @game.creator_id == @current_user.id %>
```

It's also important to note that games#update is displayed twice with two different HTTP verbs PATCH and PUT. One of the first issues that I ran into while building renecades_gameroom was making sure that each game had a stable ID. This was crucial since I had attributes seeded in the database and one simple mistake could overwrite the entire object. If I wanted to only edit a single attribute of a game, I would use PATCH. While PUT gives the user more control, it's not always necessary to send all of the parameters through again. 

Moving forward to Nested Resources, this can become overwhelming when trying to differentiate routes. In Renecades Gameroom, I encountered multiple errors because either the stack level was too deep or the resources conflicted with each other. For example while users can create their own games, it's not necessary to include games as a nested resource of users. This is because categories, tokens, and reviews are also involved in the application. 

For example if User#1 wanted to write the second review for game#1 that belongs to category#1, but was also created by #User4. This would mean that the specific review route is category/1/game/1/review/2, but what happens to the user. Instead, I use the model relationships and foreign keys in order to list the attributes for that specific review. In this application, a game has a foreign key called creator_id that corresponds to the user. Since the game also belongs to a category described the model, it no longer becomes part of the URI pattern. So now if I wanted to see the reviews for game#1, the route would be game/1/reviews. When I debug with binding.pry to make sure that the game still holds these attributes and keys, they are not affected. 

![](https://i.imgur.com/ZfECfCQ.png)
![](https://i.imgur.com/FwxXGCP.png)





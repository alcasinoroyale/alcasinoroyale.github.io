---
layout: post
title:      "Creating New Full Stack Development Projects"
date:       2020-02-10 01:07:53 +0000
permalink:  creating_new_full_stack_development_projects
---

Having recently updated components of my portfolio site, I've also started to brainstorm what types of projects that I can build to improving my development skills as well as expand my portfolio. Throughout the past few months, I've created some mini projects including a countdown timer using and a mini forum application using the Sinatra library, but they were never on the magnitude of Renecades Gameroom or Reel 2 Real.

After some thought, I decided to start crafting a worldbuilding application that would combine the needs of both an author and a screenwriter using the Ruby on Rails framework. I was inspired by other applications such as Celtx, Wattpad, Notebook.ai, and Google Docs that share similar features. Users would have the ability to personalize and store all of their story ideas in one place, write chapters and/or scripts based on those ideas, and interact and collaborate with other writers on the platform. Since this application has a lot more code than my previous portfolio projects, I've spent more time drawing the components and elements before moving into the text editor. 

Though this project is still early in development, I started working on the migrations, models, controllers, and views for the home page, signup, and login pages. Since I incorporated OAuth for Facebook logins in Renecades Gameroom, I plan to use OAuth for Google logins instead. This would be a great opportunity to not only understand how the OAuth feature works for different third party logins, but also test my development skills with a new platform. 

```
class User < ApplicationRecord
  has_secure_password
  has_many :worlds

  validates :username, :email, presence: true
  validates :password, presence: true, allow_nil: true, confirmation: true
  validates :username, :email, uniqueness: true
  validates_confirmation_of :password
end
```

For example, I've added password confirmation to the user model so that if there are errors made in the password field based on the user input, the confirmation field would be able to note the user of these errors so that they can fix them. This was an issue with one of my earlier projects because once the users were created, the process of changing the password without a recover feature was pretty extensive.

For the Signup form, I've also integrated a helper method to display errors for each attribute. Inside of the google class, I've noted 'Sign in with Google' where the oAuth feature will be utilized. It was also crucial to create classes for the fields and labels so that the elements would be structured. Finally, I provided a link to the login page in the case where a user already has an account. In addition to the attributes needed for user signup, they will also have other features on their profile such as a bio and their favorite genre.

```
<div class="sign-up">
<h1>Sign Up</h1>
<%= form_for @user do |f| %>

  <%= f.label :username, "Username", class: 'form-label' %>
  <%= f.text_field :username, class: 'form-text-box' %>
  <%= errors_for @user, :username %>

  <%= f.label :email, "Email", class: 'form-label' %>
  <%= f.text_field :email, class: 'form-text-box' %>
  <%= errors_for @user, :email %>

  <%= f.label :password, "Password", class: 'form-label' %>
  <%= f.password_field :password, class: 'form-text-box' %>
  <%= errors_for @user, :password %>
  
  <%= f.label :password_confirmation, "Confirm Password", class: 'form-label' %>
  <%= f.password_field :password_confirmation, class: 'form-text-box' %>
  <%= errors_for @user, :password_confirmation %>

  <%= f.submit "Create User", class: 'form-submit-box' %>
<% end %>
    <p>or</p>
    <div class="google">
      <%= link_to do %>
      <%= image_tag("google-icon.png") %>
      Sign in with Google
      <% end %>
    </div>
    <br>
  <br><%= link_to "Already have an account?", '/login' %>
</div>
```



---
layout: post
title:      "Comparing Signup and Login Forms"
date:       2020-02-16 23:01:21 +0000
permalink:  comparing_signup_and_login_forms
---

After building with several Ruby and JavaScript frameworks, I wanted to compare and contrast login forms across different platforms. Signup and login forms are a crucial component of any user account based application as they require authenticated credentials for access beyond the landing page. They also have a variety of options to notify the user of the overall process such as success and error messages based on the validations. Going back to some of the initial commits of my earlier projects, specifically in Ruby on Rails, I noticed that the signup and login forms were not structured with classes or ids, which made for some interesting code. 

Now that I've improved as a software engineer, building login forms has been a much easier process from the design perspective. Instead of using `<br>`, I rely on classes to organize the labels and fields. This is incredibly useful when you're using a similar structure across multiple files. Generally, the user interface for a signup and login page isn't much different and if you want consistency across your application, using the same classes would be beneficial as it will provide more time for building other features and pages. 

In my last blog post, I discussed some of the planning that goes into developing a new project and how drawing it on paper or a whiteboard could help move along the process once you enter the text editor. I think with signup forms there's a bit more discussion that occurs because user accounts will likely have more attributes than a username, email, and password. However, they might not be necessary for the signup page, especially if you're using an OAuth feature for third-party logins such as Facebook or Google. 

The creation of more personalized attributes such as your bio or contact information doesn't have to occur until your other user credentials are validated and authenticated. Users might want to explore the application more before implementing this info into their account. Recently, I've been revitalizing a vendor portal utilizing Angular and Typescript and a signup form isn't necessary because the existing accounts are retrieved from the server. However, with the login form, I needed to make sure that the application would recognize the user credentials once the vendor entered their username and password on the login page. 

```
<form [formGroup]="loginForm" (ngSubmit)="onSubmit($event)">
  <div class="form-group">
    <input id="username" type="text" placeholder="Username" class="form-control" formControlName="username" 
		ng-model="username" [ngClass]="{'submitted': submitted}">
    <div *ngIf="username.invalid && (username.dirty || username.touched)" class="alert alert-danger">    
      <div *ngIf="username.errors.required"> Username is required. </div>
    </div>
  </div>

  <div class="form-group">
    <input id="password" type="password" placeholder="Password" class="form-control" formControlName="password" 
		ng-model="password" [ngClass]="{'submitted': submitted}">
    <div *ngIf="password.invalid && (password.dirty || password.touched)" class="alert alert-danger">    
      <div *ngIf="password.errors.required"> Password is required. </div>
    </div>
  </div>

  <div class="form-group">
    <button type="submit" class="btn btn-primary btn-lg btn-block">LOG IN</button>
  </div>
</form>
```

I decided to use a `formGroup` to implement the login which requires a username and password, but they also use a form-control class inside of the inputs. Since I have the ng-model set to the specific keys, it gives me the option to check whether the username and password are invalid and clicked. If they are, it will display an alert message under the form field with a message Username/Password is required. Despite being a different framework, this is somewhat similar to the structure of my Ruby on Rails application where it will also display the error messages under the text field. 

```
  <%= f.label :username, "Username", class: 'form-label' %>
  <%= f.text_field :username, class: 'form-text-box' %>
  <%= errors_for @user, :username %>
```

The main difference is that Ruby on Rails is relying on the helper method of errors_for and the user model compared to Angular, which has the ng-model already set within the form-group. If we take a look inside a signup form of a React component, the input has a handleChange (this can be called anything) to detect whenever the text in the input changes. However, the structure of each value still has a handful of similarities in that we still assign properties such as a type, class, and name.

```
  <label>Username</label>
        <div className="control">
          <input
            type="text"
            name="username"
            placeholder="Enter username"
            value={username}
            onChange={this.handleChange}
            required
            />
        </div>
```


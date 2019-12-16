---
layout: post
title:      "Working with Angular and Typescript"
date:       2019-12-15 18:48:17 -0500
permalink:  working_with_angular_and_typescript
---


During the past few weeks, I have been learning and working with Angular and Typescript for a front-end development project. Considering that I had never built applications with the Angular framework before, I was a bit anxious for the overall experience. Having now learned the fundamentals through a variety of resources including docs and walkthroughs, it was much easier than I expected. With its similarities to React from an structural perspective, it provides a nice alternative for a client-side application. The structure is centralized around components, modules, and services and a MVC architecture. 

One of the many perks of Angular's structure is not only its organization, but also the ability of two-way data-binding and reusable code. For example, running `ng generate component header` creates a ts, html, spec.ts, and scss file. Since Typescript is a superset of Javascript, the ts file is where a lot of your functions and classes will come into play. Inside header.component.ts, we have

```
import { Component } from '@angular/core';

@Component({
selector: 'app-header',
templateUrl: './header.component.html',
styleUrls: ['./header.component.scss']
})

export class HeaderComponent {

}
```

If you wanted to implement the header into the other components, you can write `<app-header></app-header>` in the component's html file and it will automatically render the entire header. This is convenient especially when you're working across multiple files and do not want to repeat code. Another example would be displaying today's date on the app's root page. 

First, you would create a date display component and then make sure to add that specific name as an import and a declaration to app.module.ts. This file is generated as the root module of your application, working as a dashboard to group all of your components as well as modules that are downloaded from angular packages. I found this incredibly similar to React's app.js, which also stores each component to enable rendering. Some examples might include a FormsModule, a MatDialogModule, and a RouterModule where you can build the application's navigation.

```
import { AppComponent } from './app.component';
import { HeaderComponent } from './header/header.component';
import { DateDisplayComponent } from './date-pipe.component';

@NgModule({
  declarations: [
	AppComponent,
	HeaderComponent,
	DateDisplayComponent
	],
	providers: [],
	bootstrap: [AppComponent]
})
```

Inside date-display.component.ts

```
import { Component } from '@angular/core';

@Component({
  selector: 'date-display',
  templateUrl: './date-display.component.html'
  styleUrls: ['./date-display.component.scss']
})

export class DateDisplayComponent {
  today:  number = Date.now();
}
```

The component will have a template where the date will be displayed with today as the variable inside the div and heading. Now if you wanted this specific date to be part of the header, you can go to the header's html file and write `<date-display></date-display>` which will appear on each page that you have implemented the header.




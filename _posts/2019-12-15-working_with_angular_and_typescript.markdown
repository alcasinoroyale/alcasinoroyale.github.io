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


---
layout: post
title:      "Updating The Itinerary Hub"
date:       2019-10-27 19:04:53 +0000
permalink:  updating_the_itinerary_hub
---

![](https://i.imgur.com/jF6KFWu.png)

When I first built The Itinerary Hub, I heavily relied on bootstrap for the styling and functionality, but I wanted to travel back and implement some styling changes given my greater knowledge of CSS. One of the reasons that users consistently return to a specific application is not only because the features are intuitive, but they also appreciate the design. Creating a compelling user interface from scratch can sometimes be a difficult task, especially when you're working across mulitple files and have a threshold of classes and IDs. Organization and naming is crucial to knowing what the end result will be once you've made a number of changes to the CSS file. Since I've decided to utilize the main css file for all of the styling instead of bootstrap, I sketched out each focus of the application. For example, the navigation bar was one of the elements that changed signficantly from what I originally had. 

![](https://i.imgur.com/kWfVj14.png)

In the previous version, the navigation bar would overlap with "The Itinerary Hub" when you reduced the window size, but it also integrated with the page's content. Even though the MVC architecture worked successfully, the application's design only acted as a foundation of what's to come. Throughout the past few days, I've tested different code with both JS and CSS in order to fix this, but decided on the responsive menu, which has been used across a variety of applications. There are some amazing tools for building this feature, but one thing that came to mind immediately was Font Awesome. Instead of modifying the navigation menu inside layout.erb significantly, I was able to use the font awesome bars icon and some of my original code combined with JS. This was helped by a couple of tutorials I watched that offered an alternative to building a new navigation. Notably, the JS function, which allows the navbar to be responsive once the screen size changes and the links are integrated inside of the burger.

```
/// The first a element inside of the navigation class ///
      <a href="javascript:void(0);" class="icon" onclick="myFunction()">
            <i class="fa fa-bars" style="font-size:24px"></i>
      </a>
							
      <script>
         function myFunction() {
           let x = document.getElementById("myNavMenu");
           if (x.className === "navigation") {
             x.className += " responsive";
           } else {
             x.className = "navigation";
           }
         }
     </script>
```

If we take a look at the updated [CSS file](https://github.com/alcasinoroyale/the_itinerary_hub/blob/master/public/css/style.css) for The Itinerary Hub, the most significant modifications are:

```
@media screen and (max-width: 1080px) {
  .navigation a {display: none;}
  .navigation a.icon {
    display: block;
  }
}

@media screen and (max-width: 1080px) {
  .navigation.responsive {
    background-color: #235437;
    position: relative;
    margin-right: 0px;
    margin-top: 0px;
  }

  .navigation.responsive a {
    float: none;
    display: block;
    text-align: left;
  }

  .navigation.responsive .icon {
    margin-top: 10px;
  }
}
```

Once the window's width is reduced to 1080px or lower, the navigation menu will be put inside the three bars to prevent overlaping with the application heading. The links will then be displayed as a vertical block with the text aligned to the left once the user clicks on the icon. 

![](https://i.imgur.com/bxysJRn.png)
![](https://i.imgur.com/dieGDyp.png)


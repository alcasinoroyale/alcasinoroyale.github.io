---
layout: post
title:      "Updating The Itinerary Hub"
date:       2019-10-27 15:04:53 -0400
permalink:  updating_the_itinerary_hub
---

![](https://i.imgur.com/jF6KFWu.png)

When I first built The Itinerary Hub, I heavily relied on bootstrap for the styling and functionality, but I wanted to travel back and implement some styling changes given my greater knowledge of CSS. One of the reasons that users consistently return to a specific application is not only because the features are intuitive, but they also appreciate the design. Creating a compelling user interface from scratch can sometimes be a difficult task, especially when you're working across mulitple files and have a threshold of classes and IDs. 

Organization and naming are incredibly valuable to knowing what the end result will be once you have made a number of changes to the CSS file. Since I decided to utilize the main css file for all of the styling instead of bootstrap, I sketched out each focus of the application. While The Itinerary Hub doesn't have nearly as many files as my other portfolio projects, it's still important to use comments and selectors to map out the CSS file. The element that changed significantly besides the color theme was the navigation bar. 

![](https://i.imgur.com/kWfVj14.png)

In the previous version, the navigation bar would overlap with "The Itinerary Hub" when you reduced the window size, but it also integrated with the page's content. Even though the MVC architecture worked successfully, the application's design only acted as a foundation of what's to come. Throughout the past few days, I've tested different code with both JS and CSS in order to fix this, but decided on the responsive menu, which has been used across a variety of applications. 

There are some amazing tools for building this feature, but one thing that immediately came to mind was one of my favorite open source projects called Font Awesome. I've also used Font Awesome for the social media icons on my portfolio site and for the travel icons in the "Create Itinerary" form. 

Instead of modifying the navigation menu inside layout.erb significantly to make it responsive, I was able to use the Font Awesome bars icon and some of my original code combined with JS. This was helped by a couple of tutorials I watched that offered an alternative to building a new navigation. Notably, the JS function, which allows the navbar to be responsive once the screen size changes and the links are integrated inside of the bars icon.

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

If we take a look at the updated [CSS file](https://github.com/alcasinoroyale/the_itinerary_hub/blob/master/public/css/style.css) for The Itinerary Hub, the most crucial changes are:

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


---
layout: post
title:  "Learning the basics of submitting to GitHub"
date:   2017-07-30 02:32:06 -0400
---


One of the most crucial elements of beginning to learn code at The Flatiron School is getting to know GitHub and how it works. Whether you're using learn.co or terminal, it's important to remember that GitHub holds all of the respositories for your labs and lessons. For those who haven't done a single ounce of code, becoming familiar with submitting projects to GitHub can be quite tricky. Here are some simple instructions if you're just getting started. 

First, you would want to create a new directory to hold all of the project files and folders. For example, if I wanted the directory to be called "i_love_coding", I would type "mkdir i_love_coding" into my terminal. It should then pop up as a new directory in the sidebar on your computer and be ready to use. Then, you'll type cd i_love_coding to change into the new directory.

After you've switched into the directory for your new project, the first part is figuring out the motions of branches. Each project will give you the ability to use branches at your own leisure, but the initial one is the master. Anything that is in the master can be ambulatory so if you're working on a new feature for your project, it's imperative that you create a new branch. Creating branches will allow you to experiment and commit changes to GitHub that won't affect the master. This way you can save all of your code before you decide to publish it as the final product. 

In order to create a new branch, you will want to use your terminal again. Currently, it will showcase that you're on the master branch, which you'll come back to later. If I decided to name the new branch "stranger things" I would type "git checkout -b stranger_things" into my terminal. 

Similar to the directory, it will switch into the new addition to the project. Now, you'll have the ability to edit all of your files on the stranger_things branch.

Once you've successfully developed, revised, and polished the code on your specific branch, you can merge it into your master and submit it to GitHub by following these six easy steps:

1. Entering "git init" into your terminal will create a new repository. Once you've completed this step, typing "ls" will allow you to view all of the files within that directory that you can upload to the new repository. 

2. Next, you'll want to use "git status" so that you can see a list of the specific files you've modified during the production of your project. Even while you're working on your project, "git status" will help you keep track of your progress so that none of the files are misplaced.

3. Moving forward with git add . - Always use this so that you can stage all of the changes. If there is a specific file with new changes, then you would also add the filename, otherwise using "git add ." will stage all of the files that you've made changes to. For example, if I had an index.html, I would type git add . "index html" into my terminal. 

4. The fourth step is git commit -m "insert your own message here" For every commit that you submit to GitHub, you'll want to include a brief description for the file(s). Especially when you're personalizing a new branch, using commit messages is a more collaborative way of showcasing the changes.

5. In order to merge "stranger_things" with the master, you will want to type "git merge stranger_things" into your terminal. This will then lead to the final step.

6. Finally, once you've merged your branches with the master, you can then write "git push origin master" to submit the complete project to GitHub. This will push all of the changes you've made to the i_love_coding repository in your profile.

Before I started learning code, I only knew a rough sketch of HTML and CSS. Finally knowing how to use "git" definitely helped me comprehend how to track changes successfully. It's a fairly convenient control system to follow once you get the gist of it. Always make sure that when you are finally submitting changes to GitHub, all of the modified files you want are in the project directory and branch that you're on.


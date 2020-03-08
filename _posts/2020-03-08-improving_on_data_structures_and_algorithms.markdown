---
layout: post
title:      "Improving on Data Structures and Algorithms"
date:       2020-03-08 21:40:05 +0000
permalink:  improving_on_data_structures_and_algorithms
---

In my last blog post, I referenced how I've been reviewing JavaScript concepts in order to improve my critical thinking and problem solving skills. One of my main goals for March was working on Data Structures and Algorithms as they are not only a major component of technical interviews, but also a large part of refactoring and building functions for all applications. I decided to start taking a course on Udemy that focused on this and so far it's been a great experience.

Before taking the course, I used CodeWars and HackerRank to solve coding challenges, but I think it's also beneficial to return to a instructional breakdown once in a while so that you have the ability to understand how and why the solution works. I'm familiar with some of the problems that have been introduced such as The Classic Fizzbuzz, but there's always something new to solve. It's also interesting to see the various solutions to a single problem, especially ones that I would rarely think of on the first try. I think that learning and coding multiple solutions is an incredible resource to have because it showcases to the interviewer that you are going beyond the expectations and exploring other ways to refactor code. 

From conversations that I've had with other software engineers, I've consistently learned that approaching a problem in psuedo code is one of the best strategies to have. In the Anagrams section of the course, it addressed a lot of the issues that I encountered when I first started learning JavaScript, specifically for loops. I've mostly used the classic "for loop" for functions that I've built in past applications and projects ``` for (let i = 0; i < 10; i++) {...}``` so it was interesting to see the usage of a "for in" such as in the example below to check whether if the strings contained the same characters.

```
function anagrams(stringA, stringB) {
  const aCharMap = buildCharMap(stringA);
  const bCharMap = buildCharMap(stringB);
   if(Object.keys(aCharMap).length !== Object.keys(bCharMap).length) {
    return false;
   }
	 
 for (let char in aCharMap) {
  if (aCharMap[char] !== bCharMap[char]) {
   return false;
  }
 }
  return true;
}
```



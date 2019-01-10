---
layout: post
title:      "Advanced Javascript Reduce Lab"
date:       2019-01-10 05:33:13 +0000
permalink:  advanced_javascript_reduce_lab
---


I'm often hitting my head against the proverbial wall it seems when trying to solve the labs. More times than not, its some tiny thing that wastes hours of my time. Well, I shouldn't say wastes, its valuable learning (though quite frustrating). Tonight was no exception.

After a few interations, I finally got code to work in the javascript interpreter ( I run `js index.js` just to catch syntax errors, and throw some console.log statements in the code to see whats going on. In this lab we were suppose to go through an array of sentences and make a 'word count map' to show how many sentences had the same word count. And it worked beautifully... in the javascript interpreter. I could see the results right there on the console. Boy does that feel good, when you get it to work.

Then I run `learn`, and my heart sinks. How could it be failing I saw the correct results on the console. I triple check for a typo: none. What was going on, I tried several other things, and then tried moving my reduce function above the other working code, and then the working code started to fail too. But the javascript interpreter wasn't giving me an error.

It took a few more experiments, but I finally figured out I was forgetting to declare the variable in my anonymous function, The javascript interpreter didn't care (`js index.js`), but the tests were more strict.

Here is my failing code:
```
var wordCountMap = monologueLines.reduce(
  (allCount, str) => {
    cnt = str.split(" ").length;
    allCount[cnt] = (cnt in allCount) ? allCount[cnt]+1 : 1;
    return allCount;
  },  
  {}
);

```
 
I forgot the **var** on this line:

  **var** `cnt = str.split(" ").length;`

Here is my working code:
```
var wordCountMap = monologueLines.reduce(
  (allCount, str) => {
    var cnt = str.split(" ").length;
    allCount[cnt] = (cnt in allCount) ? allCount[cnt]+1 : 1;
    return allCount;
  },  
  {}
);

```
I'm posting this hoping that it helps someone else who may run into  a similar problem. 

Happy coding!

 

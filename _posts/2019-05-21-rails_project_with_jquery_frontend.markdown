---
layout: post
title:      "Rails Project with JQuery Frontend"
date:       2019-05-21 02:17:48 -0400
permalink:  rails_project_with_jquery_frontend
---


This was a continuation of my Rails Portfolio Project. So, just to recap, my wife is part of a non-profit organization that is affiliated with our church, which provides funding to start or expand business to members in third-world contries. Currenttly applications are comming in through email as scanned or photos of handwritten forms. Thus the idea was born; make an online application form that automagically saves it in a database, and make the data entry person happy-er. You can check out the demo here:
https://rocky-ocean-61079.herokuapp.com

This time around, I used bootsrap to do the layout and make the webpage responsive (works on mobile devices as well as the desktop). Bootstrap also made working with modals easy (with one caveat which we will discuss later). JQuery handles cross browser compatibilty for us and makes for concise coding. I used Devise to handle authentification. Users must select the church/region that they are responsible for during registration. when they login, applicantions that they have previously create are shown, and in the top navigation and link to create a new application is provided (along with welcome and signout).

The goal was basically a one page web-app. We used AJAX to make requests and load the data into the DOM without reloading the page. I don't think I was well prepared for this project, but I did learn alot! Here are some of challenges.

I wish we had covered event delegation in the curriclum, It allows you to avoid adding event listeners to specific nodes like when you dynamically generate parts of the DOM, those elements weren't around when your scripts were loaded, and thus the script cand attach listeners to those nodes. instead, the event listener gets added to a parent. That event listener analyzes bubbled events to find a match on child elements.

bubbled events is something I'm also a little weak on, I had to stopPropagation of of these evens to avoid double deletes.

Since rails disables forms by default to avoid accidental double submits, it took me a bit to figure out how to re-enable the form so that I could resubmit on the Asset and Household Member entry pages.

It also took me a bit to figure out how to close Bootstrap modals on form submission. I tried to do it manually in the script, but there was too much going on behind the scenes. A simple, and I thing elegant solution, was after the AJAX form submission, was to just call .click() on the modal close button and let bootstrap handle all the background stuff.

Dynamically setting the 'Edit' modal content was pretty cool. On the edit link, we used data attributs that we could read in javascript to set the values of the form inputs. I thought it was pretty clever, but I can't take credit for comming up with it, thanks Google and StackOverflow.

You can view my Video Walkthrough here: <https://youtu.be/l3CO42nmC9s>

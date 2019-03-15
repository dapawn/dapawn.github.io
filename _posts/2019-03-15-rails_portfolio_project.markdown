---
layout: post
title:      "Rails Portfolio Project"
date:       2019-03-15 19:27:01 +0000
permalink:  rails_portfolio_project
---


My wife is part of a non-profit organization that is affiliated with out church, which provides members funding to start and expand businesses in third-world contries. Currenttly all the applications are submitted through PDFs, sometimes just a scanned or photo image of the PDF, then this information must be manually entered into their database. So I thought, hey I should be able to make an only application form that automagically saves it in a database and save the day... or at least and hour here and there.

So I took a look at the applicaton form, which turns out to be pretty involved, but as with any large project, if you break it down into small pieces, it becomes manageable. So I ended up with four form entry pages, and one for review. Thie entry pages start with the applicant's person details, them one for their assets, then comes household details, and then the entry for their business request. Once submitted the application is ready for review, and Edit link is provided in each section in case any changes are needed. 

I used Devise to handle authentification. Users must select the church/region that they are responsible for during registration. when they login, applicantion the have requested are shown, and in the top navigation and link to create a new application is provided (along with welcome and signout).

TODO: some of the form quesiton only get filled out of you answer yes to a previous question, with javascript we could automagically show these types of questions when appropriate.

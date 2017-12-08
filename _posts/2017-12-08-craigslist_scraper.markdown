---
layout: post
title:      "Craigslist Scraper"
date:       2017-12-08 21:59:00 +0000
permalink:  craigslist_scraper
---


For the CLI Data Gem  Project, we were asked to scrape data from the website of our choosing, I selected Craigslist, which is an online classified ad site that I have used many times. Here are the basic tools that we use in Ruby:

## CSS Seelctors

CSS Selectors are really a topic in themselves, but lets keep things simple. In HTML there are tags like ``<img>`` and ``<p>``. you can also assign and ``id`` or a ``class`` to these or any other HTML tag, and then these help us assign our styles to the appropriate tags using CSS selectors. basically prefix a '.' to a class name, and '#' to a class, and HTML tags are just references as the are e.g. ``div`` or ``p``. 

## CGI

Craigslist search can be done right with a URL as the search terms are passed right in the URL usng the HTTP GET method. I wanted to be able to search Craigslist from the Command Line, so I needed to be able to encode the input for a URL. For example, if there were multiple words, the spaces needed to be escaped, this could be done with a simple RegEx, but to make it more flexible the Ruby CGI.escape gem to handle it all for us.

``item = CGI.escape(gets.strip)``
## Open-uri

Once we have contructed to search URL, we want to get the data into the script. Open-URI lets us do this with the open method, as easy as this:

``search_url = "https://#{city}.craigslist.org/search/sss?query=#{item}"`` <br>
``search = Nokogiri::HTML(html)``

## Nokogiri

Nokogiri (fine toothes saw in Japanese), is a ruby gem that parses the HTML and helps us scrape the informatino we need of the page, but first we need to look at the source, to see what CSS selectors we can use to pull out the information we need. This can be tricky, but the more you do it, the easier it gets.

``search = Nokogiri::HTML(html)`` <br>
``search.css("li.result-row span.result-meta span.result-hood")``

## Conclusion

Ruby gives us many tools to make scrping web pages easier. Investing a little time learning them now will reap abundant rewards down the road. 

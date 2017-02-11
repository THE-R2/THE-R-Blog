---
ID: 1412
post_title: >
  Diving Into Dynamic Website Content with
  splashr | R-bloggers
author: The-R
post_date: 2017-02-11 12:44:15
post_excerpt: ""
layout: post
permalink: >
  http://the-r.kr/2017/02/11/diving-into-dynamic-website-content-with-splashr-r-bloggers/
published: true
inline_featured_image:
  - "0"
---
<a href="https://www.r-bloggers.com/diving-into-dynamic-website-content-with-splashr/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+RBloggers+%28R+bloggers%29"><img class="alignnone size-full" src="http://the-r.kr/wp-content/uploads/2017/02/cerv.png" alt="" /></a>

Diving Into Dynamic Website Content with splashr
February 9, 2017
By hrbrmstr
inShare
3
(This article was first published on R – rud.is, and kindly contributed to R-bloggers)
Share
Tweet
If you do enough web scraping, you’ll eventually hit a wall that the trusty httr verbs (that sit beneath rvest) cannot really overcome: dynamically created content (via javascript) on a site. If the site was nice enough to use XHR requests to load the dynamic content, you can generally still stick with httr verbs — if you can figure out what those requests are — and code-up the right parameters (browser “Developer Tools” menus/views and my curlconverter package are super handy for this). Unfortunately, some sites require actual in-page rendering and that’s when scraping turns into a modest chore.

For dynamic sites, the RSelenium and/or seleniumPipes packages are super-handy tools to have in the toolbox. They interface with Selenium which is a feature-rich environment/ecosystem for automating browser tasks. You can programmatically click buttons, press keys, follow links and extract page content because you’re scripting actions in an actual browser or a browser-like tool such as phantomjs. Getting the server component of Selenium running was often a source of pain for R folks, but the new docker images make it much easier to get started. For truly gnarly scraping tasks, it should be your go-to solution.

However, sometimes all you need is the rendering part and for that, there’s a new light[er]weight alternative dubbed Splash. It’s written in python and uses QT webkit for rendering. To avoid deluging your system with all of the Splash dependencies you can use the docker images. In fact, I made it dead easy to do so. Read on!

Going for a dip
The intrepid Winston Chang at RStudio started a package to wrap Docker operations and I’ve recently joind in the fun to add some tweaks & enhancements to it that are necessary to get it on CRAN. Why point this out? Since you need to have Splash running to work with it in splashr I wanted to make it as easy as possible. So, if you install Docker and then devtools::install_github("wch/harbor") you can then devtools::install_github("hrbrmstr/splashr") to get Splash up and running with:

library(splashr)

install_splash()
splash_svr <- start_splash()
The install_splash() function will pull the correct image to your local system and you’ll need that splash_svr object later on to stop the container. Now, you can have Splash running on any host, but this post assumes you’re running it locally.

We can test to see if the server is active:

splash("localhost") %>% splash_active()
## Status of splash instance on [http://localhost:8050]: ok. Max RSS: 70443008
Now, we’re ready to scrape!

We’ll use this site — http://www.techstars.com/companies/ — mentioned over at DataCamp’s tutorial since it doesn’t use XHR but does require rendering and it doesn’t prohibit scraping in the Terms of Service (don’t violate Terms of Service, it is both unethical and could get you blocked, fined or worse).

Let’s scrape the “Summary by Class” table. Here’s an excerpt along with the Developer Tools view:



You’re saying “HEY. That has <table> in the HTML so why not just use rvest? Well, you can validate the lack of <table>s in the “view source” view of the page or with:

library(rvest)

pg <- read_html("http://www.techstars.com/companies/")
html_nodes(pg, "table")
## {xml_nodeset (0)}
Now, let’s do it with splashr:

splash("localhost") %>% 
  render_html("http://www.techstars.com/companies/", wait=5) -> pg
  
html_nodes(pg, "table")
## {xml_nodeset (89)}
##  [1] <table class="table75"><tbody>\n<tr>\n<th>Status</th>\n        <th>Number of Com ...
##  [2] <table class="table75"><tbody>\n<tr>\n<th colspan="2">Impact</th>\n      </tr>\n ...
##  [3] <table class="table75"><tbody>\n<tr>\n<th>Class</th>\n        <th>#Co's</th>\n   ...
##  [4] <table><tbody>\n<tr>\n<th class="batch_class" colspan="4">Anywhere 2017 Q1</th>\ ...
##  [5] <table><tbody>\n<tr>\n<th class="batch_class" colspan="4">Atlanta 2016 Summer</t ...
##  [6] <table><tbody>\n<tr>\n<th class="batch_class" colspan="4">Austin 2013 Fall</th>\ ...
##  [7] <table><tbody>\n<tr>\n<th class="batch_class" colspan="4">Austin 2014 Summer</th ...
##  [8] <table><tbody>\n<tr>\n<th class="batch_class" colspan="4">Austin 2015 Spring</th ...
##  [9] <table><tbody>\n<tr>\n<th class="batch_class" colspan="4">Austin 2016 Spring</th ...
## [10] <table><tbody>\n<tr>\n<th class="batch_class" colspan="4">Barclays 2014</th>\n   ...
## [11] <table><tbody>\n<tr>\n<th class="batch_class" colspan="4">Barclays 2015 Spring</ ...
## [12] <table><tbody>\n<tr>\n<th class="batch_class" colspan="4">Barclays 2016 Winter</ ...
## [13] <table><tbody>\n<tr>\n<th class="batch_class" colspan="4">Barclays Cape Town 201 ...
## [14] <table><tbody>\n<tr>\n<th class="batch_class" colspan="4">Barclays NYC 2015 Summ ...
## [15] <table><tbody>\n<tr>\n<th class="batch_class" colspan="4">Barclays NYC 2016 Summ ...
## [16] <table><tbody>\n<tr>\n<th class="batch_class" colspan="4">Barclays Tel Aviv 2016 ...
## [17] <table><tbody>\n<tr>\n<th class="batch_class" colspan="4">Berlin 2015 Summer</th ...
## [18] <table><tbody>\n<tr>\n<th class="batch_class" colspan="4">Berlin 2016 Summer</th ...
## [19] <table><tbody>\n<tr>\n<th class="batch_class" colspan="4">Boston 2009 Spring</th ...
## [20] <table><tbody>\n<tr>\n<th class="batch_class" colspan="4">Boston 2010 Spring</th ...
## ...##
We need to set the wait parameter (5 seconds was likely overkill) to give the javascript callbacks time to run. Now you can go crazy turning that into data.

Candid Camera
You can also take snapshots (pictures) of websites with splashr, like this (apologies if you start drooling on your keyboard):

splash("localhost") %>% 
  render_png("https://www.cervelo.com/en/triathlon/p-series/p5x")


The snapshot functions return magick objects, so you can do anything you’d like with them.

HARd Work
Since Splash is rendering the entire site (it’s a real browser), it knows all the information about the various components of a page and can return that in HAR format. You can retrieve this data and use John Harrison’s spiffy HARtools package to visualize and further analyze the data. For the sake of brevity, here’s just the main print() output from a site:

splash("localhost") %>% 
  render_har("https://www.r-bloggers.com/")

## --------HAR VERSION-------- 
## HAR specification version: 1.2 
## --------HAR CREATOR-------- 
## Created by: Splash 
## version: 2.3.1 
## --------HAR BROWSER-------- 
## Browser: QWebKit 
## version: 538.1 
## --------HAR PAGES-------- 
## Page id: 1 , Page title: R-bloggers | R news and tutorials contributed by (750) R bloggers 
## --------HAR ENTRIES-------- 
## Number of entries: 130 
## REQUESTS: 
## Page: 1 
## Number of entries: 130 
##   -  https://www.r-bloggers.com/ 
##   -  https://www.r-bloggers.com/wp-content/themes/magazine-basic-child/style.css 
##   -  https://www.r-bloggers.com/wp-content/plugins/mashsharer/assets/css/mashsb.min.cs... 
##   -  https://www.r-bloggers.com/wp-content/plugins/wp-to-twitter/css/twitter-feed.css?... 
##   -  https://www.r-bloggers.com/wp-content/plugins/jetpack/css/jetpack.css?ver=4.4.2 
##      ........ 
##   -  https://scontent.xx.fbcdn.net/v/t1.0-1/p50x50/10579991_10152371745729891_26331957... 
##   -  https://scontent.xx.fbcdn.net/v/t1.0-1/p50x50/14962601_10210947974726136_38966601... 
##   -  https://scontent.xx.fbcdn.net/v/t1.0-1/c0.8.50.50/p50x50/311082_286149511398044_4... 
##   -  https://scontent.xx.fbcdn.net/v/t1.0-1/p50x50/11046696_917285094960943_6143235831... 
##   -  https://static.xx.fbcdn.net/rsrc.php/v3/y2/r/0iTJ2XCgjBy.png
FIN
You can also do some basic scripting in Splash with lua and coding up an interface with that capability is on the TODO as is adding final tests and enabling tweaking the Docker configurations to support more fun things that Splash can do.

File an issue on github if you have feature requests or problems and feel free to jump on board with a PR if you’d like to help put the finishing touches on the package or add some features.

Don’t forget to stop_splash(splash_svr) when you’re finished scraping!


<blockquote>If you do enough web scraping, you’ll eventually hit a wall that the trusty httr verbs (that sit beneath rvest) cannot really overcome: dynamically created content (via javascript) on a site. If the site was nice enough to use XHR requests to load the dynamic content, you can generally still stick with httr verbs —... Continue reading →</blockquote><p>소스: <em><a href="https://www.r-bloggers.com/diving-into-dynamic-website-content-with-splashr/">Diving Into Dynamic Website Content with splashr | R-bloggers</a></em></p>
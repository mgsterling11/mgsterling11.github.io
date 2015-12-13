---
layout: page
title: "portfolio"
date: 2015-12-11 20:20
comments: true
sharing: true
footer: true
---

<a href="http://wheels-nyc.herokuapp.com/">Wheels</a> - A Rails/NYC open-data application to deliver accurate NYC taxi fare time & cost estimation
<li>Utilizes New York City Open Data API & Geocoder gem to return search results to users via flexible parameters</li>
<li>Algorithms parse historical taxi data with 4-point geolocation coordinates, providing locational search accuracy</li>
<li> Customized Google Maps Javascript API to serve an interactive map with transit directions & marked routes</li>
<li> Enables comparison to Uber/Lyft rates via Uber API & algorithms to calculate Lyft fare (no API available)</li>
<li> Visualizes data via chart of route/search’s average cost per day on an hourly basis, based on historical fares</li>
<li> Oauth login provided via Facebook & Uber to enable users to save trip history & recall previous routes</li>
<br>

<a href="http://wikiroulette.herokuapp.com">Wikiroulette</a> - A single-page Rails game that takes users on a random link clicking journey through Wikipedia
<li> Scrapes Wikipedia.com pages & continuously uploads results to a non-reloading page via AJAX requests</li>
<li> Utilizes Mechanize gem to scrape Wikipedia pages and retrieve all links from each page</li>
<li> Customized Jquery event handlers & CSS to build dynamic user interface and site design</li>
<br>

<a href="https://github.com/mgsterling11/gradepending">GradePending</a> - A Rails open-data application to view official NYC restaurant health inspection results 
<li> Utilizes New York City Open Data API to return information to users via flexible searches</li>
<li> Features Yelp API to connect users restaurant reviews/ratings; Google Maps API to display restaurant location</li>
<li> Migrated initial version of application from a local database to API reliance to source most accurate/recent data</li>
<br>
 
<a href"http://get-cookin.herokuapp.com/">Get Cookin’</a> - A Rails application to share personal recipes with friends and family
<li> Implements nested tables structure in database to perform advanced ActiveRecord queries & CRUD functionality</li>
<li> Utilizes AJAX to asynchronously perform full CRUD actions on stored recipes without page reload</li>
<li> Features user-driven permissions so that only a recipe’s creator can update/delete a recipe; features an admin page so that site developers can monitor custom analytics</li>
<li> Developed in a test driven environment to confirm table associations and other features function as expected</li>
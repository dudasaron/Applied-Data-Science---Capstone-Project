# Clustering destinations

## Introduction

### Background
International tourism is a multi billion dollar industry. Every year tens of millions of tourists visit cities internationally. Thanks to the wide range of availiable cheap air travel (well, at least before COVID-19) tourists have a plethora of cities to chose from. But every city is different and the available activities differ from region to region, culture to culture, city to city.

### Problem
Since tourist have so many options to choose from, it can be difficult to chose their next destination. By clustering cities by available leisure activities, we can narrow down the list of possible destinations to ones that are similar to cities previously visited and liked, and spare them from looking up  information on cities they most like will not like.

### Interest
The main target is obviously the tourist. But besides tourists travel agencies could also make use of such solutions for example to power recommender systems or targeted advertising. An other possible beneficiary of such informations are tourism agencies. By having this information they can compare their regions with that of their competitors and plan their strategies accordingly.


## The Data

### Data sources
For the list of the most visited cities I will use [this Wikipedia page](https://en.wikipedia.org/wiki/List_of_cities_by_international_visitors). This page aggregates data from the financial services corporation Mastercard, and the consulting firm Euromonitor. Altough this data is not the most recent (Euromonitor data is for 2018, and Mastercard data is for 2016) it will be a good starting point. Also this is the most detailed data source I found freely available on this topic.

To cluster the cities listed in the page mentioned above, I will use Foursquare's venue data. Foursquare provides location data on many different type of venues like museums, music venues, restaurants and so on. By using Foursquare's explore API I can get a list of popular venues for each city.

### Data preparation
I will need to pre-process the data to be able to handle it easly later in the training process. First I need to scrape the Wikipedia page to get a list of the cities. After that I need to get the list of venues for each city. After the list of venues is ready for each city it is necessary to check the data, and filter out any invalid data or possibly cities with too few venues. The data will still need some preparation: in order to find similar cities, the venue data must be aggregated for each city: selecting only the top N categories per city (where N is an integer to be determined later).  Then depending on the selected model the data may still need some preparation like normalization, or one-hot encoding.

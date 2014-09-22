---
layout: post
title: "You Know Nothing Jon Sno<sub>x</sub>w"
date: 2014-09-22 20:00
comments: true
categories: 
---

This blog post has the best game of thrones/weather/air quality joke you'll read all day. It also has some notes on what I built at [the BathHacked Air Quality hackday](http://www.bathhacked.org/news/air-quality-hack-20-september/).

<!-- More -->

Going into the hackday I realised several things.

![My helpful screenshot](/images/jon-snow.jpg)

Firstly, there was a lot of data available. BANES council had made an archive of [13 years of air quality data available](https://data.bathhacked.org/Environment/Historical-Air-Quality-Sensor-Data/37nn-vnib). I'd also discovered that [the DEFRA Air Quality data archive had data for one sensor](http://uk-air.defra.gov.uk/networks/site-info?uka_id=UKA00306) dating from 1997. That's a lot of data to get to grips with. I decided that I was going to focus on trying to summarise the dataset rather than build anything on top of it.

Secondly, I also didn't really know anything about air quality. To get prepared I [produced some documentation for everyone attending the hackday](http://www.bathhacked.org/datastore/air-quality-fast-start/) that summarised the main data source, and provided some useful pointers. I also did some reading around on both the BANES and [UK-AIR](http://uk-air.defra.gov.uk/) websites.

Air quality data analysis is a complex area. There are a lot of factors to take into account including a variety of sources of pollutants, complex interactions between pollutants and impacts from the prevailing weather conditions. BANES publish some summary reports but while informative they didn't really give me a sense of where the pollution was coming from, or how bad it was at different types of the day or year.

I also discovered the [Open Air](http://www.openair-project.org/) project which provides an [R](http://www.r-project.org/) package to support air quality analysis. It also comes with an amazing set of documentation: the manual is over 200 pages and includes a short introduction to R. 

So I read the manual and went into the hack day with a goal of trying to answer two questions:

1. Can we provide Bath citizens with more insight into the air quality for Bath?
2. Can we provide the local council with new ways to generate meaningful visualisations and summary reports?

I didn't get as far as I'd hoped, but I managed to do enough to create what I think is [an interesting summary of the data](http://datasulis.org/air-quality-report/london-road-aurn.html). 

Using R and `openair` I was able to quickly import, normalise and explore the data. In fact R makes it so easy to generate diagrams that I spent a lot of the day just [playing with graphs](http://treasure.diylol.com/uploads/post/image/587658/resized_all-the-things-meme-generator-graph-all-the-things-9ec157.jpg).

The judges also liked the results and I was lucky enough to [win the Most Educational Project prize](http://www.bathhacked.org/news/and-the-results-are-in/). The report is now [featured on the BANES website](http://www.bathnes.gov.uk/services/your-council-and-democracy/local-research-and-statistics/wiki/historic-air-quality). 

I've also [published the code on github](https://github.com/datasulis/air-quality-report) if you'd like to explore. The main report code could easily be customised to use an alternate DEFRA location if you want to try it on some data from your local area.

There's more to explore here, not just around the data analysis, but also around the concept of having reproducable data analytics. 

Reproducability is an important part of scientific research and analysis. At least one driver of the growing adoption of open source and open data in the research community is to make science more reproducable: it should be possible for someone else to pick up your research to easily check the results and maybe go a step further.

I've not yet seen this idea extended to publishing of analysis of open (statistical) data, but the concepts are the same. Reproducability is another way to increase transparency. Open data has been shown to help people find data errors, but open source can also help people find and fix errors in an analysis itself.

I'll certainly be playing more with R over the coming months. I'm sold on the ease with which it's possible to really quickly explore a dataset.

The other hacks produced on the day were all really interesting. I recommend you read [the run down of the entries on the BathHacked blog](http://www.bathhacked.org/news/and-the-results-are-in/).




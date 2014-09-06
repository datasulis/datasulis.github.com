---
layout: post
title: "Exploring a Bath Chronicle house price story"
date: 2014-09-06 11:01:32 +0100
comments: true
categories: 
---
The cover of the Bath Chronicle caught my eye yesterday. The headline article was "House prices now 8 times average pay" you can [read a summary of the article on their site](http://www.bathchronicle.co.uk/Average-house-price-Bath-times-average-salary/story-22858365-detail/story.html). The article describes that the TUC are reporting that the ratio of house price to salary in Bath & North East Somerset has increased 89% between 1997-2013

I wondered where the data for this analysis came from and whether it would be possible to repeat it using open data. So I picked up a copy of the Chronicle, opened my web browser and explored further.

<!-- More -->

Firstly before we dig deeper I'll state up front that I have no political agenda here, or any particular interest in criticising the Chronicle. What I want to do is see whether the data reported in the article is available and whether the facts are correct. If we can highlight some inaccuracies or come up with some interesting insights along the way, then great.

To summarise, the key statements facts from the article are as follows:

* The ratio of house price to salary in 1997 was 4.62
* The ratio of house price to salary in 2013 the ratio was 8.74 (89% higher than 1997)
* Across the South West the average ratio is now above 5
* The Bank of England will now be [limiting the number of risky mortages](https://www.gov.uk/government/news/help-to-buy-mortgage-guarantee-loans-new-lending-limits), assessed as those with a ratio higher than 4.5
* Cotsworld is the most unaffordable area in the South West with a ration of 11.6

The article also includes some notes on most and least affordable places in the UK. But it was the following quote that made my raise my eyebrow:

>"The TUC has been unable to release the figure for the average house price or the average salary in B&NES, because that data, which the study is based on, is not available from the Government"

Unfortunately that statement is simply not true. I can't tell whether this is a misunderstanding on behalf of the reporter in the Chronicle or a mis-communication from the TUC. Like most newspapers the Chronicle doesn't link to its sources. But after some searching I found [a TUC report on prices in the North West](http://www.tuc.org.uk/economic-issues/britain-needs-pay-rise/social-issues/housing/house-prices-across-half-north-west-now), but not one specifically on the South West.

But I know that the statement is not true because all of the raw data required to calculate these averages and the resulting ratio is available as open data:

* The Land Registry have been publishing their [price paid data](http://landregistry.data.gov.uk/) as open data for some time. The available data goes back to 1995. So we have the price of every house sale in B&NES for nearly 20 years.
* The ONS [Annual Survey of Hours and Earnings](http://www.ons.gov.uk/ons/rel/ashe/annual-survey-of-hours-and-earnings/index.html) (ASHE) provides information on earnings across the UK and data is available from 1998 to 2013, although the latest figures are still provisional. There's a [visualisation of changes in weekly earnings by region](http://www.neighbourhood.statistics.gov.uk/HTMLDocs/dvc138/index.html). 

So the raw data necessary to re-calculate the figures reported by the Chronicle and the TUC is available as open data for anyone to re-use. 

But not only that, the Department of Communities and Local Government (DCLG) actually publishes [detailed figures on the housing market](https://www.gov.uk/government/statistical-data-sets/live-tables-on-housing-market-and-house-prices) which includes the ratio of house prices to salary! This appears to be the actual source of the data and is actually linked to from the TUC report on the North West. Reading the Chronicle article though you might be lead to assume that the TUC have produced some analysis using unreleased data, when in fact the source is the government themselves.

The data we're interested is included in [Table 577: ratio of median house price to median earnings by district, from 1997](https://www.gov.uk/government/uploads/system/uploads/attachment_data/file/321017/Table_577.xlsx). There's also a PDF containing charts that [plots the changes across the entire country](https://www.gov.uk/government/uploads/system/uploads/attachment_data/file/321015/Chart_576.pdf). Looking at that data we can confirm all of figures reported in the article.

Not only that, but because we have access to the actual underlying data we can also take into account a few caveats that ONS and DCLG include in their supporting notes. None of these invalidate the figures, but may be useful when interpreting them. For example we can learn that:

* the ASHE is based only on 1 per cent sample of employee jobs
* the ASHE only includes data from employers, so it doesn't cover self-employed people
* the reporting regions are based on district boundaries from 2009, so changes to size/shape of districts since that date won't be reflected
* the 2013 figures are still provisional and are subject to change

Perhaps most importantly though we can see the entire set of data on the ratio of house prices to salary for B&NES from 1997 to 2013. I've taken a copy of that data and [uploaded it to the Bath Hacked data store](https://data.bathhacked.org/Economy-and-Jobs/Ratio-of-house-prices-to-earnings-since-1997/gbqi-3ffv). I've used that to create the graph shown below:

<div><iframe width="500px" title="Changes in media house price to earnings ratio" height="425px" src="https://data.bathhacked.org/w/v4tc-6xs9/?cur=kbjUpZMvAfS&from=root" frameborder="0" scrolling="no"><a href="https://data.bathhacked.org/Economy-and-Jobs/Changes-in-media-house-price-to-earnings-ratio/v4tc-6xs9" title="Changes in media house price to earnings ratio" target="_blank">Changes in media house price to earnings ratio</a></iframe><p><a href="http://www.socrata.com/" target="_blank">Powered by Socrata</a></p></div>

As you can see the ratio has increased significantly since 1997 with the largest increases in the period between 1999-2004. Interestingly the ratio seems to have dropped slightly over the last few years: the provisional figure for 2013 is similar to that for 2004.

So as a result of the exercise I've learnt something about the data that wasn't reported in the Chronicle. Clearly the ratio is still very high but somewhat encouragingly the local trend in prices and earnings suggests the ratio is flattening out, so we're not suffering from a runaway increase over the last few years. Whether that is based on changes to house prices or salaries isn't immediately clear, but we can dig into the data further to find out.

I was also able to highlight an inaccuracy in the article: far from withholding figures the government is providing a lot of useful data in this area.

Hopefully this is useful for others too and highlights some of the possibilities for using open data from a local perspective. The Bath Hacked store could become a useful source of information for adding important context to local news stories and economic trends.

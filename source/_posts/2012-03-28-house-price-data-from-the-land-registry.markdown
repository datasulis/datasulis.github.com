---
layout: post
title: "House Price Data from the Land Registry"
date: 2012-03-28 20:15
comments: true
categories: 
 -geography
---
Like the Ordnance Survey, the Land Registry have recently started to [publish some Open Data][1]. That data includes statistics on transactions made against the Land Registry database as well as "price paid" data.

As [the Land Registry website explains][2], this data relates to:

>residential property sales in England and Wales that are lodged with us for registration. The data includes:

>* the full address of the property (Primary addressable object name (PAON), Secondary addressable object name (SAON), street, postcode, locality (if available), town, district, county)
>* the price paid for the property
>* the date of transfer
>* the property type (Detached, Semi, Terraced, Flat/Maisonette)
>* whether the property is new build or not
>* whether the property is freehold or leasehold.

We can filter their data to grab just the Bath prices.

<!-- More -->

There is a simple script in [this github project][3] which looks at the Land Registry website and grabs whatever CSV files are available. The CSV files are then read and filtered to just grab the data that relates to properties in the BA1 and BA2 area.

Currently the Land Registry are publishing this data on a monthly basis, so there is only a single month available currently. I expect that more data will appear over time. Here's [how it looks today][4].

For more background on the codes used in the data then [read the Land Registry FAQ][5].

[1]: http://www1.landregistry.gov.uk/market-trend-data/public-data
[2]: http://www1.landregistry.gov.uk/market-trend-data/price-paid-data
[3]: https://github.com/datasulis/bath-house-prices
[4]: https://github.com/datasulis/bath-house-prices/blob/master/data/bath-house-prices.csv
[5]: http://www1.landregistry.gov.uk/market-trend-data/faqs#m18

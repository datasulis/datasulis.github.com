---
layout: post
title: "The NHS in Bath"
date: 2012-03-28 19:20
comments: true
categories: 
- geography
- health
---
The [NHS Organisation Data Service][1] has a responsibility to help various parts of the NHS, and affiliated organisations, exchange information as efficiently as possible. Part of that activity involves maintaining a database of organisations relevant to the NHS. That includes everything from NHS Primary Care Trusts through to individual Pharmacies.

Their data is published under the Open Government License so can be freely reused. Lets take a look at what it contains and how we can grab a local extract.

<!-- More -->

If you visit the [ODS Website][1] you can see that they publish a large number of CSV files that contain data about organisations and their relationships. The structure of the CSV files is well-documented and the files are well-normalised so they're easy to process.

Some of the data is [updated on a weekly basis][2]. This is the core NHS organisational data. Other data, such as that [listing GPs and Branch Surgeries][3] is updated less frequently.

The data is useful for two reasons:

* If you want to draw maps showing, e.g. location of pharmacies then there's well normalised address data that can be geocoded.
* If you want to link up government statistics with individual medical practices or service providers, then you'll need the unique identifiers

I've previously taken all of the ODS data and [loaded it into Kasabi][4]. Kasabi is my day job: its a data marketplace for hosting and publish data. If you want to query the data online then you could use any of the range of APIs available from there. Sign-up is free.

For the purposes of the DataSulis project we're only really interested in the data about the NHS in Bath, i.e. BA1 and BA2. I wrote [some Ruby scripts][5] to download the latest ODS files and then extract those organisations that have the relevant postcodes. The filtered CSV files are then cached locally. You could use them as the basis for further processing.

To illustrate the output I've put [a snapshot of the data into github too][6]. For example here's a CSV file containing a list of the [Dental Practices in Bath][7]

[1]: http://www.connectingforhealth.nhs.uk/systemsandservices/data/ods
[2]: http://www.connectingforhealth.nhs.uk/systemsandservices/data/ods/datafiles
[3]: http://www.connectingforhealth.nhs.uk/systemsandservices/data/ods/genmedpracs
[4]: http://kasabi.com/dataset/nhs-organization
[5]: https://github.com/datasulis/bath-nhs
[6]: https://github.com/datasulis/bath-nhs/tree/master/data
[7]: https://github.com/datasulis/bath-nhs/blob/master/data/nhs-ods-egdpprac.csv

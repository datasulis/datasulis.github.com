---
layout: post
title: "Bath Postcodes"
date: 2012-03-27 14:06
comments: true
categories: 
- geography
---
If we're going to be working with local data then it makes sense to have a list of local postcodes. There's all kinds of data that can be usefully linked or combined based on postcode information. For example you could aggregate statistics on crime rates or house prices. Happily the Ordnance Survey now publish some useful Open Data about UK postcodes. 

So lets look at how we can work with their data to query it and extract it for local use.

<!--More-->

Here's a quick primer on postcodes. Postcodes have a structure to them. Each of the different parts of a postcode refer to a different area and those areas have a hierarchical relationship. Here are some examples along with the name that the Ordnance Survey (OS) uses to describe them: 

- [BA](http://data.ordnancesurvey.co.uk/id/postcodearea/BA) = Post Code Area
- [BA2](http://data.ordnancesurvey.co.uk/id/postcodedistrict/BA2) = Post Code District
- [BA2 3](http://data.ordnancesurvey.co.uk/id/postcodesector/BA23) = Post Code Sector
- [BA2 3PL](http://data.ordnancesurvey.co.uk/id/postcodeunit/BA23PL) = Post Code Unit

So "BA2 3PL" is within a sector called "BA2 3", and so on. The OS publish their data in various ways, including as [Linked Data](http://en.wikipedia.org/Linked_Data). Without going into details, Linked Data is just a way to publish data to the web by giving everything a unique URL. 

So based on a postcode or part of a postcode you can build a URL to the OS website and use it to grab some data. For example here's [a JSON description of BA23PL](http://data.ordnancesurvey.co.uk/doc/postcodeunit/BA23PL.json). That means that you can quickly lookup some useful data such as the lat/long which is the centre of a post code, or to discover in which electoral ward it lies. More on those alternate geographic regions in another post.

Sometimes though you just want a to grab some data for local processing. Having a list of local postcodes can help drive some address matching or other data processing task. So how can we get a complete list of local postcodes?

The OS allow you to [download data from their site](http://www.ordnancesurvey.co.uk/oswebsite/products/os-opendata.html), so you could grab all of the postcode dataset and process it to extract what you need. But there's a simpler way. The OS also provide an API called a "SPARQL Endpoint" for their data. SPARQL is a query language for working with RDF, its basically a way to query a graph of Linked Data to extract the bits you need.

Here's a SPARQL query that will fetch data about all of the Post Code Units that are within the BA1 or BA2 Post Code Districts:

{% gist 2220182 %}

If we submit that query to the [OS SPARQL Endpoint](http://api.talis.com/stores/ordnance-survey/services/sparql) then extract just the data we need.

Here's some simple Ruby code that does exactly that. It requests that the SPARQL API return the data as JSON and then spits it out as a simple CSV file.

{% codeblock Postcodes to CSV lang:ruby %}
require 'rubygems'
require 'json'
require 'net/http'
require 'cgi'
require 'csv'

dir = File.dirname(__FILE__)

query = File.read( File.join(dir, "..", "rq", "list-bath-postcode-units.rq") )

Net::HTTP.start('api.talis.com') do |http|
  req = Net::HTTP::Get.new("/stores/ordnance-survey/services/sparql?output=json&query=#{CGI.escape(query)}") 
  response = http.request(req)
  postcodes = JSON.parse( response.body )   
  CSV.open( File.join(dir, "..", "data", "bath-postcodes.csv"), "w") do |csv|
    postcodes["results"]["bindings"].each do |postcode|
      csv << [ postcode["id"]["value"], postcode["code"]["value"], postcode["latitude"]["value"], postcode["longitude"]["value"] ]
    end
  end
end
{% endcodeblock %}

Here's another version that generates a JSON description instead.

{% codeblock Postcodes to JSON lang:ruby %}
require 'rubygems'
require 'json'
require 'net/http'
require 'cgi'

dir = File.dirname(__FILE__)

query = File.read( File.join(dir, "..", "rq", "list-bath-postcode-units.rq") )

Net::HTTP.start('api.talis.com') do |http|
  req = Net::HTTP::Get.new("/stores/ordnance-survey/services/sparql?output=json&query=#{CGI.escape(query)}") 
  response = http.request(req)
  postcodes = JSON.parse( response.body )
  output = {
    "postcodes" => {}
  }
  postcodes["results"]["bindings"].each do |postcode|
    output["postcodes"][ [ postcode["code"]["value"] ] ] = {
      "id" => postcode["id"]["value"], 
      "latitude" => postcode["latitude"]["value"], 
      "longitude" => postcode["longitude"]["value"]
    }
  end
  File.open( File.join(dir, "..", "data", "bath-postcodes.json"), "w") do |file|
    file.puts JSON.pretty_generate(output)
  end
end
{% endcodeblock %}

And here are the generated files as both [CSV](https://github.com/datasulis/bath-postcodes/raw/master/data/bath-postcodes.csv) and [JSON](https://github.com/datasulis/bath-postcodes/raw/master/data/bath-postcodes.json). Those files are provided to save you re-generating them yourself but you shouldn't assume they're always going to be up to date.




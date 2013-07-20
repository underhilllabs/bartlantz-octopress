---
layout: post
title: "XPath Notes"
date: 2013-05-05 19:21
comments: true
categories: [Data Analysis, XML] 
--- 

This spring I took [Introduction to Databases](https://class2go.stanford.edu/db/Winter2013) a MOOC (Massive Open Online Class) from Stanford's Jennifer Widom. It was very interesting, I learned a great deal from it. And one of the sections of the class that I really enjoyed, even though it sounded like it was going to be pretty dry, was the section on XML. I took quite a few pages of notes on the different XMl tools, so I figured I might as well post them to my blog.

## XPath Definition
> XPath is a query language for selecting nodes from an XML document.

[from Wikipedia](http://en.wikipedia.org/wiki/XPath)

### XML for the Examples
``` xml countries.xml
<countries>
  <country name="Afghanistan" population="22664136" area="647500">
    <language percentage="11">Turkic</language>
    <language percentage="35">Pashtu</language>
    <language percentage="50">Afghan Persian</language>
  </country>
  <country name="Albania" population="3249136" area="28750"/>
  <country name="Algeria" population="29183032" area="2381740">
    <city>
      <name>Algiers</name>
      <population>1507241</population>
    </city>
  </country>
</countries>
```

### Basic Path
Selects all of countries from the country root node.
``` xquery
doc('countries.xml')/countries/country
```

<!--more-->
### Path with Alternation
This will select countries with populations that speak Pashtu or Swedish.
``` xquery
doc('countries.xml')/countries/country[language(Pashtu|Swedish)]
```

### Attributes are prepended with "@"
This will select the names of all countries
``` xquery
doc('countries.xml')/countries/country/@name
```

### Path with Conditional
Select the names of all countries that have a population of less than 1,000,000.
``` xquery
doc('countries.xml')/countries/country[@population < 1000000]/@name
```

### Complex Conditional
Select all countries that have a population of less than 1,000,000.
``` xquery
doc('countries.xml')/countries/country[@population < 1000000 and city/population > 50000]
```

### data() prints out just the text value.
``` 
doc('countries.xml')/countries/country[@population < 1000000]/data(@name)
```


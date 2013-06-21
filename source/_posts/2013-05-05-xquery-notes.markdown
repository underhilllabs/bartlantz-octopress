---
layout: post
title: "XQuery Notes"
date: 2013-05-05 21:44
comments: true
categories: [Data Analysis, XML]
---

This post continues my notes from [Introduction to Databases](https://class2go.stanford.edu/db/Winter2013), a MOOC taught by Stanford's Jennifer Widom. The topic of this post is XQuery.

## XQuery Defition
{% blockquote wikipedia http://en.wikipedia.org/wiki/XQuery from Wikipedia %}
XQuery is a query and functional programming language that is designed to query collections of XML data.
{% endblockquote %}

## XQuery Syntax: FLWOR 
``` xquery FLWOR Syntax
for $var in expr
let $var := expr
where expr
order by expr
return expr
```

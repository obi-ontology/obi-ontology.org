---
layout: default
title: Information content entities
permalink: /docs/data-ice/
toc: false
sidebar:
  nav: "docs"
---

An **['information content entity'](http://purl.obolibrary.org/obo/IAO_0000030)** (ICE) is a ['generically dependent continuant'](http://purl.obolibrary.org/obo/BFO_0000031) (GDC) that **['is about'](http://purl.obolibrary.org/obo/IAO_0000136)** some thing. Because it is a GDC, an ICE can be copied from one ['material information bearer'](http://purl.obolibrary.org/obo/IAO_0000178) to another. Examples: an "['age since planting measurement datum'](http://purl.obolibrary.org/obo/OBI_0001156) 'is about' some ['Spermatophyta'](http://purl.obolibrary.org/obo/NCBITaxon_58024)" (among other things); a "['minimal inhibitory concentration'](http://purl.obolibrary.org/obo/OBI_0001514) 'is about' some ['dose response curve'](http://purl.obolibrary.org/obo/OBI_0001172)", another ICE.  Aboutness axioms should reinforce the content of term definitions.  

<img align="right" src="/assets/images/docs/data-ice/data_ice_branch.png">

The 'information content entity' **['data item'](http://purl.obolibrary.org/obo/IAO_0000027)** class holds singular entities or collections of entities that specifically record inputs or outputs of processes / equipment / human interaction. OBI distinguishes the following types of data items, usually called "datums", as follows:

* A **['measurement datum'](http://purl.obolibrary.org/obo/IAO_0000109)** class names and models the datum outputs of an assay, and their contextual semantics. 
* A **['settings datum'](http://purl.obolibrary.org/obo/IAO_0000140)** class which enables modeling an apparatus control input.
* A **['predicted data item'](http://purl.obolibrary.org/obo/OBI_0302867)** class that applies to output of a ['prediction'](http://purl.obolibrary.org/obo/OBI_0302910) process.

A data item (aka datum) may have an associated ['value specification'](http://purl.obolibrary.org/obo/OBI_0001933) that holds an XSD Literal numeric, date, time, string, URI, or categorical value which can be matched or if scalar, compared, using axioms.  Alternately, an ICE class may have a textually-encoded, parsable ['has representation'](http://purl.obolibrary.org/obo/OBI_0002815) data property that points to any XSD Literal value such as the string "20g" or "Every thursday" that would require further processing to separate into value specification content.  More on this to come.

<center><img src="/assets/images/docs/data-ice/data_ice_branch2.png"></center>

(Diagram: [data-ice.drawio](https://www.draw.io/#Uhttps%3A%2F%2Fobi-ontology.org%2Fassets%2Fimages%2Fdocs%2Fdata-ice%2Fdata-ice.drawio))


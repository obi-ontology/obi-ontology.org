---
layout: default
title: Information content entities
permalink: /docs/data-ice/
toc: false
sidebar:
  nav: "docs"
---

All information items that are derived from material entities (i.e. statements that reference material qualities and are factual claims about an entity) fall under the domain of **['information content entity'](http://purl.obolibrary.org/obo/IAO_0000030)** (ICE), very generally defined as a type of entity which bears information about something<sup>1</sup>.  Any ICE class may have **['is about'](http://purl.obolibrary.org/obo/IAO_0000136)** object relations that connect it to other material entities or ICEs which define its _aboutness_.  Examples: an "['age since planting measurement datum'](http://purl.obolibrary.org/obo/OBI_0001156) 'is about' some ['Spermatophyta'](http://purl.obolibrary.org/obo/NCBITaxon_58024)" (among other things); a "['minimal inhibitory concentration'](http://purl.obolibrary.org/obo/OBI_0001514) 'is about' some ['dose response curve'](http://purl.obolibrary.org/obo/OBI_0001172)", another ICE.  Aboutness axioms should reinforce the content of term definitions.  

<img align="right" src="/assets/images/docs/data-ice/data_ice_branch.png">

The 'information content entity' **['data item'](http://purl.obolibrary.org/obo/IAO_0000027)** class holds singular entities or collections of entities that specifically record inputs or outputs of processes / equipment / human interaction. OBI distinguishes the following singular types of data items, usually called "datums", as follows:

* A **['measurement datum'](http://purl.obolibrary.org/obo/IAO_0000109)** class names and models the datum outputs of an assay, and their contextual semantics. 
* A **['settings datum'](http://purl.obolibrary.org/obo/IAO_0000140)** class which enables modeling an apparatus control input.
* A **['predicted data item'](http://purl.obolibrary.org/obo/OBI_0302867)** class that applies to output of a ['prediction'](http://purl.obolibrary.org/obo/OBI_0302910) process.

A datum may have an associated value, captured in a ['value specification'](http://purl.obolibrary.org/obo/OBI_0001933) or a ['has representation'](http://purl.obolibrary.org/obo/OBI_0002815) that points to any XSD datatype Literal value. More on this to come.

***
<sup>1</sup>The ability of an ICE to bear information depends on the coding scheme and copyable medium it inheres in, hence it is a generically dependent continuant.

(Diagram: [data-ice.drawio](https://www.draw.io/#Uhttps%3A%2F%2Fobi-ontology.org%2Fassets%2Fimages%2Fdocs%2Fdata-ice%2Fdata-ice.drawio))

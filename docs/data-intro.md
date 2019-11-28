---
layout: default
title: Introduction to OBI data modelling
permalink: /docs/data-intro/
toc: true
sidebar:
  nav: "docs"
---

OBI can be used to provide detailed descriptions of test subjects, their qualities, assays measuring those qualities, and the resulting measurements. Consider this example "John's mass is 70kg":

<img align="right" src="/assets/images/docs/data-intro/data_john_mass_context.png">
([john-examples.drawio](https://www.draw.io/#Uhttps%3A%2F%2Fobi-ontology.org%2Fassets%2Fimages%2Fdocs%2Fdata-intro%2Fjohn-examples.drawio))

The five ovals in four colors help divide the diagram into broad categories:

- the subject John (green), who is a ['material entity'](http://purl.obolibrary.org/obo/BFO_0000040)
- John's mass ['quality'](http://purl.obolibrary.org/obo/BFO_0000019) (yellow)
- the mass measurement assay (blue), which is a ['planned processes'](http://purl.obolibrary.org/obo/OBI_0000011)
- the measurement datum (gray), which is an ['information artifact'](http://purl.obolibrary.org/obo/IAO_0000030)
- the "70kg" part of the measurement, called a 'value specification', which is another sort of 'information artifact'

In the following sections we discuss each oval, the various classes (boxes) and arrows (object properties and data properties) within it.


## Material entities and their properties/qualities

Under 'material entity' we find OBI's ['organism'](http://purl.obolibrary.org/obo/OBI_0100026) class, which has the taxon ['Homo sapiens'](http://purl.obolibrary.org/obo/NCBITaxon_9606) as a descendant. The dashed arrow between 'Homo sapiens' and 'organism' indicates that several intermediate classes have been omitted from the diagram. John is an instance of the class 'Homo sapiens', which means he is also an instance of 'organism' and 'material entity'.

John has a particular ['mass'](http://purl.obolibrary.org/obo/PATO_0000125) quality. We link John to his mass quality with the ['has quality'](http://purl.obolibrary.org/obo/RO_0000086) object property. This is an "assertion" or "Abox" statement about instances. We could also assert that any instance of 'material entity' 'has quality' some 'mass' -- this would be an "Tbox" or "terminology" statement about classes. As an ontology, OBI focuses on Tbox (class-level) statements, and your data that uses OBI terms will usually focus on Abox (instance-level) statements. This diagram focuses on John and his mass and distinguishes the Abox from the Tbox.

<img src="/assets/images/docs/data-intro/data_john_mass_entity_property.png">


---
layout: default
title: Data Properties
permalink: /docs/data-properties/
sidebar:
  nav: "docs"
---

In addition to study design, protocol and execution, OBI aims to describe the field-level data of resulting datasets, which are currently likely to be found in text files, relational databases, or spreadsheets, and which need to be transformed into a RDF triple store structure to bring out the best analytic power of OBI, BFO, and other OBO Foundry ontologies.

Diagrammed on the left side are typical examples of field data related to a research subject, and on the right are datatypes that OWL reasoners and SPARQL querying engines can work with.   

<img align="right" src="/assets/images/docs/data_raw.png">

A given datum value from the left may match one of three scenarios:

#### OWL RDF/XML datatype compatible

OBI can generally express rdf/xml data type values associated with ICE enties using a triple in the form "[ICE] `has xsd:Literal value` [value]".  This covers common OWL-compatible [XML datatype schema](https://www.w3.org/TR/xmlschema-2/#built-in-datatypes) options, which can be further divided into:

- `has owl:real value` for a datum whose textual content represents a number that is unit-less.  Has owl:real range.
   - `has xsd:decimal value` subclass for unitless decimal values.
   - `has xsd:integer value` subclass for counts and other unitless integers.

- `has xsd:anyURI value` for a datum which contains a URI pointing to a document or other type of resource file.  Has xsd:anyURI range.

- `has xsd:dateTime value` for a datum containing a xsd:dateTime formatted date or time. Has xsd:dateTime range.
- Similarly, a `has xsd:dateTimeStamp value` for a date or time that includes a time zone.

- `has xsd:boolean value` for a datum which is represented as a yes/no or true/false value. Has xsd:boolean range.

#### Value specification compatible

A value that can be placed on a numeric or categorical scale. In this case a [`value specification`](/docs/data-vs) instance can be set up for it. For example:

- A duration of 20 days.

- The strings "20g", "20 grams", and "0.02kg" may differ by string comparison, but can be translated into an equivalent or identical RDF triple store value + unit using OWL ontology vocabulary. All variants can be translated into the atomic components found on the right - a decimal 20.0 and a "gram" mass unit . 

- A categorical variable like color can match selections from a list or branch of ontology terms (e.g. terms from a standardized color wheel). (Synonyms can be handled under this category too, e.g. "sienna, sepia, umber, terra cotta" -> `brown`)

#### String representation compatible 
A datum value that has some (symbol) information in it that may or may not fit directly on a numeric or categorical scale; further parsing may yeild a data structure of more atomic components. It may be an identifier which can be compared with other values for a match. Use a `string representation` to hold "undigested" data (say, in preparation for parsing by SPARQL etc.; other directives may be provided to enable interpretation of the datum's value).  For example:

- The address "16500 Mullholland Dr., Los Angeles, CA, USA" needs parsing to extract house/apartment number, street, city, country, etc.

- The fictitious Social Security Number "000-11-2222", an identifier which is not really on a scale or a categorical value. It is essentially atomic; it serves a data matchmaking role.

- An ICE [`analytical cytology data file`](http://purl.obolibrary.org/obo/OBI_0000210) specification ["https://onlinelibrary.wiley.com/doi/epdf/10.1002/cyto.990110303"](https://onlinelibrary.wiley.com/doi/epdf/10.1002/cyto.990110303)

- "20g" may be held as a value representation en route to becoming a value specification.

OBI uses `has xsd:string representation` for textual content that may or may not be parsed further, i.e. it may be coded linguistically or computationally. Has xsd:string range. Suitable for identifiers, linguistic content (words, phrases, sentences with optional OWL language facet, and strings representing scalars like "20 g".

### Data Property Implementation Approaches

Before we detail the use of `has rdfs:Literal value` etc. and `has specified value` data properties, we will discuss OBI's philosophy about data properties in general. 

<img align="right" src="/assets/images/docs/data_lee_data_property_age.png">

An ontology **`data property`** is a relation from an entity instance straight to some literal datatype value (an RDF number, string or date for example) that is a measure/estimate of what that data property is about. In an ontology one might find a `has age` data property used to express that Lee's age is 12, as shown to the right. OBI shies away from this approach, as explained below.  

<br clear="right">

<img align="right" src="/assets/images/docs/data_lee_data_property_ages.png">

The label of the data property tells humans in hopefully plain language what the value is about, but a reasoner will have a bad time guessing what the relation is equivalent to in other graphs that have differently named or identified relations that mean the same thing.  As shown, the problem is magnified if other age quantities are involved.

<br clear="right">

<img align="right" src="/assets/images/docs/data_age_measurement_datums.png">

In fact there are many kinds of [`ages`](http://purl.obolibrary.org/obo/OBI_0001167) in the biomedical and biological research realm; a number of related datums from OBI are listed here. Rather than creating a litany of data properties, OBI has chosen an alternative approach - a data modelling vocabulary that focuses on describing a core entity's role, quality, information content and other descriptive components rather than directly connecting semantically opaque data properties. This is not to say non-OBI `data properties` are forbidden in application ontologies - but going through the exercise of defining them in terms of a generic BFO/OBI/OBO Foundry set of terms may help anticipate data sharing issues.

Below is an example focusing on providing values for information content entities typically connected to a person instance.

<img src="/assets/images/docs/data_lee_has_specified_value.png">

OBI uses data properties in a limited way, via `has [xml/rdf/owl datatype] value`, [`has specified value`](http://purl.obolibrary.org/obo/OBI_0002135), and [`has specified numeric value`](http://purl.obolibrary.org/obo/OBI_0001937), and relies on the subject of the relation to provide `aboutness` semantics.  This approach reduces the amount of language needed to describe entities, at the cost of a bit more structure. *Most importantly it enables entities to be the focus of semantic elaboration (axioms) rather than being surrounded by opaque relations.* The `aboutness` details have the extra benefit of facilitating appropriate data exchange between ontology-driven systems.  By specifying that a string field is about a first name or a last name, maiden name, full name, SIN number, postal code, etc. this 'aboutness' information can guide the merging and federated querying of triple store graphs.

## Missing values

Data sources may mark missing values in a variety of ways - by an empty string, or a hyphen instead of a number or date for example.  Instance subject-verb-object triples don't have an equivalent way to express this. However there are a few ways one could indicate missing values.

- An entity's object property lacks a `has specified value` relation where one is expected.

- For an instance value being described by a `categorical value specification` (CVS) class, if that value matches the CVS class's expressed  `specifies value of` target, then no choice has been made, and no information is carried.

## Suitable object properties

It is straightforward to see a material entity connected to a pertinent quality via `has quality`, but there are other object properties that connect a material entity to other types of things:

- **More broadly, an information content entity (ICE) [`inheres in`](http://purl.obolibrary.org/obo/RO_0000052) material entity or material entity [`bearer of`](http://purl.obolibrary.org/obo/RO_0000053) ICE if the ICE is calculated from qualities of the material entity ????????**

- Thing [`denotes`](http://purl.obolibrary.org/obo/IAO_0000219) material entity if the thing is a type of **identifier**, such as a [`centrally registered identifier symbol`](http://purl.obolibrary.org/obo/IAO_0000577) like a [`specimen identifier`](http://purl.obolibrary.org/obo/OBI_0001616) or a NCIT [`identifier`](http://purl.obolibrary.org/obo/NCIT_C25364) for example.

- Material entity [`located in`](http://purl.obolibrary.org/obo/RO_0001025) geospatial reference.  Note the editor's note: "Most location relations will only hold at certain times, but this is difficult to specify in OWL." 

One can also use cardinality to specify more than one data property is allowed or required. However, some OWL reasoning profiles don't work with cardinality.

Now, back to the age example, it seems we could supply various age measurements like so:

<img src="/assets/images/docs/data_lee_object_property_ages.png">

To summarize, rather than establish a `has age` data property, OBI expresses that [`age`](http://purl.obolibrary.org/obo/PATO_0000011) is a quality of our entity, and then focuses on defining the semantics of it and its subclasses.  

However, there are some limitations of data properties that this diagram and the one below expose.

<img align="right" src="/assets/images/docs/data_lee_data_properties.png">

- A data property can't include a unit directly, so a second data property is needed for that.  Is Lee a 12 year old youth, or a 12 month old toddler?  We need the **unit of measure**, in minutes, days, months, or years.  In the example diagram of Lee's data properties to right, is the `has weight` decimal value given in kilos or grams? Is height in meters or centimetres? Without an explicit unit, assumptions are made about units associated with a data property that may work internally to a system, but are likely to fail when exchanging information with other systems.

- A data property doesn't support a relevant time of measurement value.  For example, when was Lee's `has height` observed, and was it the same time as `has weight`, such that an accurate BMI can be calculated?  Admittedly, time differentiated data is rather complex to model in OWL. A pragmatic approach, if workable, is to only expose to an OWL reasoner data that doesn't need to be differentiated by time. In the BMI example, we could assume height and weight data properties are adequately close in time that derivative calculations are ok. OBI does offer annother approach detailed in the `Time-stamped data` section to describe n-dimensional points that include time.

- A data property cannot directly specify the range of ontology term choices (which are classes or individuals) for a categorical value since data property ranges can only be drawn from xml/rdf data types. "Lee `has handedness` "http://purl.obolibrary.org/obo/PATO_0002201^^xsd:anyURI"" but the URI could point to anything on the internet. We can't express in OWL that the 'has handedness' data property URI range must fall within the class of PATO `handedness`.

- There is no direct way to indicate that an instance of paricular data property has a missing value since its object must have some value.  The data property as a whole could be omitted, and this may be sufficient for querying purposes.

To answer the above needs, OBI introduced an additional `value specification` entity, as detailed in the next section.
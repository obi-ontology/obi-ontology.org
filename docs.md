---
layout: default
title: DRAFT Documentation
permalink: /docs/
sidebar:
  nav: "docs"
---

[//]: # (Please put comments like this one into the text to communicate with other OBI-ers)
**This documentation is under active development.**

This user manual is designed to explain the core functionality of OBI for newcomers, and to serve as a canonical reference for OBI developers.

- **[Core Class Definitions](/docs/core-classes/)**: the components of a biomedical investigation

- **[ROBOT Templates](/docs/robot-intro)**: design patterns for certain branches of OBI

More background and detail on OBI terms and functionality is available in papers listed on the [Media](/media/) page.

We prefer to use [draw.io](http://draw.io) for diagrams, and we store both the source code and resulting image in the GitHub repository for this site. A few visual design principles are at work: The diagrams usually skip relation cardinality details (e.g. "X 'is about' {some / all / max 3 / only} Y"), but these do exist in OBI to enforce more structure, and are detailed in OWL code examples.  Process inputs and outputs generally flow left to right; superclass/subclass is-a relations are vertical, and upper-level categories of entity are color-coded.

In the documentation, the first usage of an ontology term such as ['patient role'](http://purl.obolibrary.org/obo/OBI_0000093) is hyperlinked to its PURL (permanent URL) web addresses for easy reference, usually on the Ontobee lookup servce where its position in the class hierarchy is shown, as well as equivalency and other subclass axioms, synonyms, definition, etc.

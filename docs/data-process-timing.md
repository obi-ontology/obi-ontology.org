---
layout: default
title: "Process timing"
permalink: /docs/process-timing/
toc: true
sidebar:
  nav: "docs"
---

## Marking process start, end and duration

Process timing can be abstractly conveyed via the dependencies established between processes using `has specified input` and `has specified output`.  However, for experimental protocols, plans, or in observed results it may be necessary to indicate specific start and end times and process durations.

### ISSUES:
- Do we allow 'has date representation' data property with xsd:datetime ?
- Do we allow `is duration of` for start, end and duration? Do we make them qualities (e.g. birth date = (start date and quality of mammal ...) and then use `has quality` relation?

<img src="/assets/images/docs/data_process_datetime.png">

<img src="/assets/images/docs/data_process_datetime_context.png">

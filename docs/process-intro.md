---
layout: default
title: "Process model basics"
permalink: /docs/process-intro/
toc: true
sidebar:
  nav: "docs"
---

[//]: # (Please put comments like this one into the text to communicate with other OBI-ers)

Generally a **[`process`](http://purl.obolibrary.org/obo/BFO_0000015)** can have other processes as parts, and can have instances with start and end times associated with them.  A **[`planned process`](http://purl.obolibrary.org/obo/OBI_0000011)** is carried out by one or more agent participants (devices, people, even organizations) who are guided by a **[`plan specification`](http://purl.obolibrary.org/obo/IAO_0000104){:target="_blank"}**, an ICE which has **[`objective`](http://purl.obolibrary.org/obo/IAO_0000005)** and **[`action`](http://purl.obolibrary.org/obo/IAO_0000007)** components. A **[`study design`](http://purl.obolibrary.org/obo/OBI_0500000)** and its **[`protocol`](http://purl.obolibrary.org/obo/OBI_0000272)** part(s) are subclasses of `plan specification`. This is documented in the [`Core Classes`](/docs/core-classes/) page.

<img src="/assets/images/docs/obi_process.png">

The above diagram illustrates various entities and relations surrounding a process.  The list of specified inputs and outputs - material entity, information content artifact, and energy, may appear individually in axioms of particular material transformation, chemical reaction, and or information processing classes.  The diagram also shows how roles can be used to differentiate inputs to a process.  Metadata about a process, including when it started or ended, or its duration, is not itself input or output but rather can be associated with the process via "aboutness".



A **process / datum model diagram** shows how material entities or data items can be an input or output of some process. This diagram often includes parts of entity property diagrams in order to reference components as inputs or in aboutness clauses.

<img align="right" src="/assets/images/docs/data_assay.png">

The **[`assay`](http://purl.obolibrary.org/obo/OBI_0000070)** process diagram to right details axioms that enable types of assay to inherit requirements: [paraphrasing] that an assay input is a material entity playing an evaluant role, and that an assay outputs one or more data items.

<br clear="right">

The next example shows a **[`mass measurement assay`](http://purl.obolibrary.org/obo/OBI_0000445)** which takes in some material and outputs a **[`mass measurement datum`](http://purl.obolibrary.org/obo/IAO_0000414)**.  The output datum is stated to be a measure of (only) mass quality. The **[`is quality measurement of`](http://purl.obolibrary.org/obo/IAO_0000221)** object property is actually a sub-property of `is about` which is used when the target of aboutness is a quality.

<img src="/assets/images/docs/data_john_mass_process.png">

The Abox shows John as an input (standing on a scale, say), and documents that a `mass measurement datum` has been taken by the `mass measurement assay`. A process modeller can work at this more abstract level, avoiding references to specific protocols or instruments involving, say, units of measure. Alternately, by merging process modelling with specific value specifications (described below), we can describe particular equipment used in an experimental protocol or execution - say a brand and model of weight scale that is only capable of measuring in grams. (That level of detail promotes an ontology-driven plug-and-play future of equipment selection and protocol design.)

## Processes with inputs playing roles

**Mark's doctor/patient interaction event example here....**

Processes can have other participants besides inputs and outputs, such as operators and material consumables.


## Process parts

Here is a representation of a patient's HPV status, adapted from ["Ontology-Enhanced Representations of Non-image Data in The Cancer Imaging Archive"](http://ceur-ws.org/Vol-2285/ICBO_2018_paper_37.pdf). It illustrates that one may want to record the input to a subprocess and the output of a more abstract process, in this case involving an assay as part of a diagnostic process.

<img src="/assets/images/docs/data_patient_hpv_status.png">


## Material processing

<img align="right" src="/assets/images/docs/data_processed_material.png">

Processes don't necessarily generate information products.  The OBI [`material processing`](http://purl.obolibrary.org/obo/OBI_0000094){:target="_blank"} class covers many kinds of process such as sample preparation, manufacturing, and staining. [`Processed specimen`](http://purl.obolibrary.org/obo/OBI_0000953){:target="_blank"} is likely needed as part of experimental protocol modeling involving biosamples. It remains a material entity, rather than a `data item` that assays output.

## Process and function

The relationship between the triumverate of a planned process, function, and device (or other performer of the process) may need clarification, especially since in math and computer science domains a function takes on input/output process details and does not come with a semantic formalism to describe what it is about, and may be entirely random.  OBI Planned process and BFO function are similar in that both ultimately depend on material entities over time, may have parts, and have an objective (a planned process has an 'objective specification' that specifies some 'process endpoint', while function objectives are left to a function definition and axiomatization to describe.)  

In OBI, a device can commit by way of the **'has function'** relation to a class of objective that it can fulfill.  An 'incubator' 'has function' some 'environmental control function'.  Functions define intentional design objectives - WHAT a device or other "bearer" of the function achieves - while a planned process models HOW such a transformation is achieved through time.  If a device is broken, one questions how its process model fails to meet its design objective.

In OBI the temporal and input/output details of HOW a function's objective is achieved are sequestered to a planned process by way of the **'inheres in'** relation.  Function definitions may include context, e.g. "the function of amylase **in saliva** to break down starch into sugar".  Function examples may reference the intentional design or biological entity that bears the function: "the function of a hammer to drive in nails".  Functions may have parts, like "'information prrocessor function' has part some 'consume data function'". 

Depending on how abstractly a function is defined, e.g. "pumping function", it may inhere in a variety of devices, each with its own process.  **This allows the unification of function objective and planned process objective in a number of cases?**

A rock can be used as a hammer, and so can be a participant in a hammering process. This distinguishes an intentional USE of the rock as a hammer, from the intentional DESIGN of it (if any) for some purpose. A planned process can swap out a rock for a hammer in many cases as a device. So, for a planned process, a choice of participant may be available - one which has a function stated that fulfills an 'objective specification' (functional requirement) directly, or one which axiomatically fulfills a functional requirement but was not intentionally or biologically evolved to do so.  Referencing "function" of some material entity then, appears only to add information that a material entity was intentionally designed or evolved to meet some purpose, but otherwise doesn't preclude use of other material entities to meet the same objective specification.


# Overview of PSDI metadata
* Date: 2024-10-14
* Modified Date: 2024-10-14
* Content custodian: Aileen Day (University of Southampton)
* Authors: Aileen Day (University of Southampton)

## Summary
The PSDI metadata describes the [Physical Sciences Data Infrastructure (PSDI)](https://www.psdi.ac.uk/ ) project.  
This is its working version.
The metadata is made available in [JSON-LD](https://json-ld.org/) format, and guidance files describing for anyone who wants to use or contribute to it are available in the [https://github.com/orgs/PSDI-UK/guidance/](https://github.com/orgs/PSDI-UK/guidance/) folder.
A major source of guidance and reference in structuring and populating this metadata was version 1 of  [Cross-Domain Interoperability Framework (CDIF)](https://worldfair-project.eu/):
* [vocabulary.jsonld](./vocabulary.jsonld) corresponds to the CORE CONTROLLED VOCABULARY profile
* [resource-catalogue.jsonld](./resource-catalogue.jsonld) corresponds to the CORE DISCOVERY profile

## Background reading
1. [Cross-Domain Interoperability Framework (CDIF)](https://worldfair-project.eu/cross-domain-interoperability-framework/ )
2. [JSON-LD Best Practices](https://w3c.github.io/json-ld-bp/ )


## Dependencies

The public website deployed by this project depends on the assets made public by PSDI's "css-template" at https://psdi-uk.github.io/css-template/. Any changes to these assets will be reflected in this project's website, and this project should ideally be tested with any changes before they're made live. An issue with retrieving these assets will appear as the website appear unstyled and missing its header and footer.

In case these assets become no longer available for some reason, the commit `517e74b99fba4920c4eea4b17131fdd42eb93f72` can be used as a reference to restore local versions of them.

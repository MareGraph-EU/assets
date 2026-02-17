# MAREGRAPH Semantic Assets

![MAREGRAPH Logo](https://www.maregraph.eu/img/maregraph-text-horizontal-600x200.svg)

## Overview

This repository hosts a comprehensive network of **semantic assets** — including OWL ontologies, SKOS controlled vocabularies, SHACL validation shapes, and a DCAT-based data catalogue — designed and developed in the context of the [MAREGRAPH](https://www.maregraph.eu/) project.

Together, these assets lay the foundations for **semantic interoperability in the marine biodiversity domain** by establishing formal, reusable, and extensible semantic data models for representing and interlinking marine biodiversity information.

In particular, the **MAREGRAPH ontology network** provides a modular and standards-based framework for publishing, validating, and integrating biodiversity data as Linked Open Data.

### About MAREGRAPH

Co-funded by the European Union under the Digital Europe Programme, [MAREGRAPH](https://ec.europa.eu/info/funding-tenders/opportunities/portal/screen/opportunities/projects-details/43152860/101100771) focuses on the creation of an **open Semantic Knowledge Graph for marine biodiversity**.

By leveraging the **Semantic Web** stack, the project enhances the *Findability, Accessibility, Interoperability, and Reusability* (**FAIRness**) of foundational **High-Value Datasets (HVDs)** concerning aquatic biodiversity.

### Core data sources

![MAREGRAPH](./img/maregraph.png?raw=true)

The MAREGRAPH ontology network harmonizes and interlinks data from three authoritative pillars of marine biodiversity information:

* **[MarineRegions](https://www.marineregions.org/):** a standard register of georeferenced marine place names and maritime areas with their geographical features
* **[WoRMS](https://www.marinespecies.org/)**: the World Register of Marine Species, a comprehensive register of names of aquatic organisms and associated taxonomic and descriptive information
* **[EurOBIS](https://www.eurobis.org/)**: the European Ocean Biogeographic Information System, a central repository for species occurrence and distribution data across European waters.

## Repository Structure

This repository is organized to support the full lifecycle of semantic engineering—from conceptual modeling to data validation.

For the ontology modules we follow a modular versioning pattern to ensure backward compatibility and stable URI resolution for the MAREGRAPH ontology network.

```text
.
├── catalog.ttl                  # DCAT-based catalog describing all semantic assets
├── graphical-representation/    # Master Graffoo source files (.graphml) for all ontology modules
├── shacl-shapes/                # SHACL constraint files (one per ontology module)
└── ontologies/                  # Root for all OWL-serialized domain models
    ├── [module-name]/           # e.g., taxon-name, distribution, media
    │   ├── v0.1/                # Specific version snapshot
    │   ├── v0.2/
    │   ├── ...
    │   └── latest/              # Copy of the most recent stable release
    │       ├── module.owl       # OWL RDF/XML serialization
    │       ├── module.rdf       # RDF/XML serialization
    │       ├── module.ttl       # Turtle serialization
    │       ├── module.png       # Graffoo diagram
    │       ├── README.md        # Module description
    │       └── module.html      # Auto-generated HTML documentation (pylode)
    └── ...
```

### Key components

📂 `ontologies/`

The core of the repository with the **ontology modules**. Each module is partitioned by version. The `latest/` directory always contains the current stable release, including multiple serializations (Turtle, RDF/XML, etc.) and human-readable documentation.

📂 `shacl-shapes/`

Contains the **SHACL** files used to validate instance data against the MAREGRAPH models. There is a 1:1 mapping between ontology modules and their corresponding shape files to ensure data integrity.

📂 `graphical-representation/`

Contains the editable **Graffoo** source files (`.graphml`). These diagrams provide the formal visual mapping of classes, properties, and axioms, serving as the primary visual design reference.

📄 `catalog.ttl`

A machine-readable Turtle file with a **DCAT**-based specification of the **MAREGRAPH data catalog**. This asset provides metadata for every semantic asset (including the ontologies in this repo, Liked Data Event Streams produced using the ontologies, etc.), enabling automated harvesting by open data portals and federated registries.

## The MAREGRAPH Ontology Network

The MAREGRAPH ontology network is designed as a modular network of interconnected components, ensuring a separation of concerns while maintaining a unified view of marine biodiversity data. The architecture follows a multi-layered approach, balancing specialized domain knowledge with broad cross-domain interoperability.

Building upon previous work that led to define the [Marine Regions Ontology](http://marineregions.org/ns/ontology) and publishing the Marine Regions gazetteer as [Linked Data Event Streams](https://www.marineregions.org/feed), MAREGRAPH introduces specialized ontology modules for:

* **Names, taxonomy and biology**: formalizing the naming of taxa, their geographic distribution, ecological traits, and associated scientific literature as curated in **WoRMS**.
* **Biogeographic observations**: representing species occurrences in space and time, including sampling events and other activities, biological measurements, and environmental parameters recorded in **EurOBIS** datasets.

The development of the MAREGRAPH ontology network follows a rigorous, requirement-driven ontology engineering lifecycle. A comprehensive description of the ontology engineering methodology—including the elicitation of functional requirements, the definition of domain-specific use cases, and the formalization of Competency Questions—is documented in detail in [Deliverable D3.2 - Final ontology design and development](). This deliverable also provides the technical rationale for specific design choices, architectural patterns, usage examples, and the strategies used to align the network with existing ontologies.

![MAREGRAPH ontology network](./img/maregraph-ontology-network.png?raw=true)

### Semantic architectural layers

To ensure technical robustness and semantic clarity, the network operates across three strategic layers:

1. **Top Level Layer:** Provides base and common cross-domain classes and properties, reused by the other ontology modules.
2. **Domain Layer:** The core modules that capture specific knowledge areas in the marine biodiversity domain.
3. **Alignment and Reuse Layer:** The top level and domain modules maintain direct and indirect alignments with established ontologies and international standards to ensure maximum interoperability. Key alignments include:
    - **Foundational:** D0, DOLCE+DnS Ultralite (DUL).
    - **Domain models and standards:** Darwin Core (DwC), Bioschemas, SOSA (Sensor, Observation, Sample, and Actuator), OpenBiodiv-O (the OpenBiodiv ontology), and the Environment Ontology (ENVO).
    - **Other standard for data and metadata:** Schema.org, SKOS/SKOS-XL, Dublin Core.

### Core ontology modules

The network is organized into thematic modules that correspond to the primary data dimensions of the marine biodiversity domain.

#### Top Level

**URI**: [`https://aphia.org/ns/top-level`](https://aphia.org/ns/top-level)

The [`top-level`]() ontology module provides base and common cross-domain classes and properties, such as identifiers, source references, and units of measure, reused by the other ontology modules in the network.

#### Taxon Name

**URI**: [`https://aphia.org/ns/taxon-name`](https://aphia.org/ns/taxon-name)

The [`taxon-name`]() ontology module handles scientific and vernacular names, taxonomic status, ranks, and classification hierarchy for aquatic organisms.

#### Distribution

**URI**: [`https://aphia.org/ns/distribution`](https://aphia.org/ns/distribution)

The [`distribution`]() ontology module defines geographic distribution, occurrence origin, type locality, and invasiveness for marine species. It relies on the [Marine Regions Ontology](http://marineregions.org/ns/ontology) for representing geographical locations.

#### Media

**URI**: [`https://aphia.org/ns/media`](https://aphia.org/ns/media)

The [`media`]() ontology module allows representing metadata for images, videos, and other media objects related to marine species.

#### Attribute and Trait

**URI**: [`https://aphia.org/ns/attribute-trait`](https://aphia.org/ns/attribute-trait)

The [`attribute-trait`]() ontology module allows representing biological, ecological, and taxonomic characteristics—ranging from body size and habitat to IUCN conservation categories—for marine species.

The [`https://aphia.org/ns/traits/`](https://aphia.org/ns/traits/) SKOS controlled vocabulary defines the attributes and traits originating from WoRMS.

#### Marine Observation

**URI**: [`https://eurobis.org/ns/marine-observation`](https://eurobis.org/ns/marine-observation)

The [`marine-observation`]() ontology module allows representing and relating species occurrences, events (e.g., cruises, sampling activities, etc.), and associated measurements or facts covering biotic and abiotic properties.

By modelling species observations, this module allows integrating and linking EurOBIS, WoRMS, and MarineRegions data.

### Usage and Linked Open Data production

The MAREGRAPH ontology network serves as the formal foundation for the production and publication of **Linked Open Data**. These models are thus actively used to transform and harmonize large datasets into machine-readable formats.

#### Linked Data Event Streams (LDES)

A primary application of these ontologies is the publication of **Linked Data Event Streams** ([LDES](https://w3id.org/ldes/specification)). This approach allows consumers to synchronize with the data sources and track changes over time. The MAREGRAPH ontologies provide the necessary semantics to describe the core entities (species names, taxa, events, observations, etc.) within these streams.

By accessing the following feeds, developers and data scientists can see concrete examples of how the ontologies are used to represent complex marine biodiversity data.

* **WoRMS/Aphia LDES Feed:** [`https://aphia.org/feed`](https://aphia.org/feed)
  * **Example:** *Engraulis encrasicolus* (Linnaeus, 1758) | [WoRMS](https://www.marinespecies.org/aphia.php?p=taxdetails&id=126426) :arrow_right:
	[`https://aphia.org/id/taxname/126426`](https://aphia.org/id/taxname/126426)
* **EurOBIS LDES Feed:** [`https://eurobis.org/feed`](https://eurobis.org/feed)
  * **Example:** Type locality distributions from the World Register of Marine Species | [https://marineinfo.org/id/dataset/5184](https://marineinfo.org/id/dataset/5184) :arrow_right:
	[`https://eurobis.org/id/dataprovider/5184`](https://eurobis.org/id/dataprovider/5184)
* **MarineRegions LDES Feed:** [`https://www.marineregions.org/feed`](https://www.marineregions.org/feed)

### Reusability and extensibility

While the design of these assets is informed by the proven data models of WoRMS and EurOBIS, the resulting ontologies are engineered as much as possible for **domain-wide application**. They serve as a generalized, extensible foundation for any stakeholder aiming to publish or consume **Linked Open Data** within the biodiversity sector.

## The MAREGRAPH data catalog

To provide a machine-readable entry point to the project's outputs, we have defined a formal [data catalog](https://w3id.org/marine/metadata/catalog) using the **Data Catalog Vocabulary** ([DCAT](https://www.w3.org/TR/vocab-dcat-3/)) and the **Asset Description Metadata Schema** ([ADMS](https://semiceu.github.io/ADMS/releases/2.00)).

The MAREGRAPH DCAT-based data catalog describes the datasets, data services, and semantic assets produced within the project and in related initiatives.

By following the **DCAT Application profile for data portals in Europe** ([DCAT-AP](https://semiceu.github.io/DCAT-AP/releases/3.0.1/)), this catalog ensures that our ontologies and high-value datasets can be automatically harvested by the European Data Portal and other federated metadata aggregators.

The MAREGRAPH catalog acts as a central hub and provides metadata about the ontology modules and controlled vocabularies that enable representing the knowledge domains covered by WoRMS, EurOBIS and MarineRegions.

The catalog also describes the related **Linked Data Event Streams** ([LDES](https://w3id.org/ldes/specification)) feeds. These services ensure the continuous synchronization of data, exposing changes over time for WoRMS, EurOBIS, and MarineRegions datasets.


## License and Attribution

The semantic assets and documentation in this repository are released under the following licenses:

* [![CC BY 4.0](https://mirrors.creativecommons.org/presskit/buttons/80x15/svg/by.svg)](https://creativecommons.org/licenses/by/4.0/) **Ontology modules and documentation:** Licensed under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) license.
* [![CC0 1.0](https://mirrors.creativecommons.org/presskit/buttons/80x15/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/) **Metadata and vocabularies:** As specified in the [catalog](https://w3id.org/marine/metadata/catalog), certain metadata assets and SKOS vocabularies are dedicated to the public domain under the [Creative Commons CC0 1.0 Universal (CC0 1.0)](https://creativecommons.org/publicdomain/zero/1.0/) license.

If you use the MAREGRAPH ontology network or its related assets in your research, software, or data products, please provide attribution to the MAREGRAPH project and the contributing institutions.

**Suggested Citations:**
* Lodi, G., Russo, A., Nuzzolese, A.G., Poggi, F., Portier, M., Van Maldeghem, L., Van Hoorne, B., Dekeyzer, S. (2025). **D3.2 – Final ontology design and development.** Zenodo. [https://doi.org/10.5281/zenodo.15593409](https://doi.org/10.5281/zenodo.15593409)
* Lodi G, Russo A, Goley J, Portier M, Exter K (2024) **The European MAREGRAPH Project: Enhancing Marine Data Interoperability through Semantic Knowledge Graphs.** *Biodiversity Information Science and Standards* 8: e136697. https://doi.org/10.3897/biss.8.136697


## Contributing and community engagement

We welcome contributions from domain experts and the Semantic Web community to help improve the MAREGRAPH ontology network. Anyone is free to contribute by identifying errors or inconsistencies, suggesting new terms, or proposing improvements to the models.

To ensure all changes are tracked and discussed transparently, we use **GitHub Issues** as our primary communication channel.

* **Report a Bug:** Notice an inconsistency in an OWL module or a broken link?
* **Suggest an Improvement:** Have an idea for a more descriptive property or a new class?
* **Request a Feature:** Need an extension to support a specific biodiversity use case?

To contribute or ask your question, **[open a new issue](https://github.com/MareGraph-EU/assets/issues/new/choose)** in this repository. Please provide as much detail as possible following the available template(s) where applicable.

Additional details about the availability and maintenance of the semantic resources included in the [data catalog](https://w3id.org/marine/metadata/catalog) are provided in [this section](./catalog_resource_maintenance.md).

---

**Have you used the MAREGRAPH ontologies?**

We are committed to the continuous improvement of these assets and would love to learn more about your use case. Whether you are using the ontologies for academic research, commercial applications, or public sector data integration, your feedback is invaluable to us.

If you are using these models or have stories to share regarding your integration process, needs and use cases, please reach out to us: :email: [info@maregraph.eu](mailto:info@maregraph.eu)

## Governance and Maintenance

The semantic assets in this repository were designed and developed by the **Institute of Cognitive Sciences and Technologies** of the **Italian National Research Council** ([CNR-ISTC](https://www.istc.cnr.it/)), in collaboration with and under the expert guidance and support of the **Flanders Marine Institute** ([VLIZ](https://vliz.be/en)).

To ensure that these assets remain a reliable foundation for the global research community:

* **Long-term maintenance:** VLIZ is committed to the long-term maintenance and sustainability of the MAREGRAPH semantic assets beyond the initial project lifecycle.
* **URI persistence:** All namespaces and identifiers are managed to ensure permanent resolution within the Linked Data ecosystem.
* **Institutional support:** As the host of WoRMS and EurOBIS, VLIZ provides the institutional stability necessary to keep the underlying infrastructure fully operational.

## Maintenance of resources mentioned in `catalog.ttl` 

This document outlines where the main resources mentioned in [catalog.ttl](https://raw.githubusercontent.com/MareGraph-EU/assets/refs/heads/main/catalog.ttl) are maintained and where they're available.  

### 1. Catalog

- **Description:** The description of catalogs  contains structured metadata about marine resources and observations.  
- **Source:** _catalog.ttl_ file in [this GH repository](https://github.com/MareGraph-EU/assets/) 
- **Available at:** [`https://w3id.org/marine/metadata/catalog`](https://w3id.org/marine/metadata/catalog)
- **Update Flow:**
  1. updates should be pushed to `catalog.ttl` file.  

### 2. Ontologies

- **Description:** Ontologies define semantic relationships between marine entities, traits, and observations.  
- **Source:** files in _./ontologies/_ folder in [this GH repository](https://github.com/MareGraph-EU/assets/)
- **Available at:** 
  - [`https://aphia.org/ns/attribute-trait`](https://aphia.org/ns/attribute-trait)
  - [`https://aphia.org/ns/distribution`](https://aphia.org/ns/distribution)
  - [`https://eurobis.org/ns/marine-observation`](https://eurobis.org/ns/marine-observation)
  - [`https://aphia.org/ns/media`](https://aphia.org/ns/media)
  - [`https://aphia.org/ns/taxon-name`](https://aphia.org/ns/taxon-name)
  - [`https://aphia.org/ns/top-level`](https://aphia.org/ns/top-level)

- **Update Flow:**
  1. Ask for updates via new GH issues.  
  2. If approved, updates will be pushed to `/ontologies` folder.  
  3. Updates to the ontology can be visualized on their respective identifier.

### 3. Traits Vocabulary

- **Description:** Controlled vocabulary for species traits.  
- **Source:** Internal database published on [Aphia.org](https://www.aphia.org/)  
- **Available at:** [`aphia.org/ns/`](https://www.aphia.org/ns/)   
- **Update Flow:**
  1. contact ... for add/update to traits (definitions).
  2. If approved, Updates will be applied to the internal Aphia database, according to internal release procedures.  
  3. Updates version of traits is available on [aphia.org/ns/](https://www.aphia.org/ns/)   

### 4. Marine Regions ontlogy 

- **Description:** Geospatial boundaries for marine regions.  
- **Source:** [Lifewatch GH repository](https://github.com/lifewatch/marineregions-ontology)
- **Available at:** [`marineregions.org/ns/ontology`](http://marineregions.org/ns/ontology)
- **Update Flow:**
  1. Ask for updates via new GH issues.  
  2. If approved, updates will be pushed to `ontology.ttl` (and/or `shapes.ttl`) file.  
  3. The updated ontology can be visualized on [marineregions.org/ns/ontology](http://marineregions.org/ns/ontology).


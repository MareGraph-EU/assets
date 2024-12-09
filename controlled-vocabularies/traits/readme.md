# Controlled Vocabulary of WoRMS Attributes & Traits  

This repository provides the RDF representation (in Turtle syntax) of a controlled vocabulary for WoRMS (World Register of Marine Species) attributes and traits.  

## Resources  

- **Attributes and Traits List**:  
  A publicly available list of WoRMS attributes and traits can be accessed here:  
  [WoRMS Attributes & Traits List](https://marinespecies.org/traits/aphia.php?p=attrdefinitions)  

- **Dependency Visualization**:  
  The relationships and dependencies between traits are visualized in the following document:  
  [Visualization of Trait Dependencies](visualization_attributes_dependencies.pdf)  

## Folder Structure  

The traits in this repository are organized into two folders:  
- **terms**: Contains traits that can be represented as simple, independent lists of concepts.  
- **_tmp_concepts_with_dependencies**: Contains traits that have dependencies on other traits and require additional modeling efforts to represent their relationships accurately.  

## Additional Work Required  

The dependency visualization highlights that while some traits can be modeled as straightforward lists of concepts,  
Other traits (listed in **./_tmp_concepts_with_dependencies**) necessitate more advanced modeling to account for their interdependencies. 

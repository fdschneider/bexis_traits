# Ecological Traitdata Standard
Florian D. Schneider, Nadja Simons, Caterina Penone, Andreas Ostrowski  
12 Mai 2017  


**This is the documentation of the Ecological Traitdata Standard (ETS), version 0.3** 

This defined vocabulary aims at providing all essential columns for raw data of functional trait measurements for ecological research. 

Most terms relate to terms from the Darwin Core Standard and Extensions (Names compliant with DWC are referenced thus in field 'Refines'; the full Darwin Core can be found here: http://rs.tdwg.org/dwc/terms/index.htm)

The data standard is ordered into a **core section** with essential columns for trait data, extensions which are allowing to provide additional layers of information, as well as a vocabulary for metadata information of particular importance for trait data. A final section provides defined terms for lists of trait definitions, also termed a Trait Thesaurus. 

Extensions:

- the `Occurence` extension contains information on the level of individual specimens, such as date and location and method of sampling and preservation, or physiological specifications of the phenotype, such as sex, life stage or age. 
- the `MeasurementOrFact` extension takes information at the level of single measurements or reported values, such as the original literature from where the value is cited, the method of measurement or statistical method of aggregation. 
- The extension `BiodiversityExploratories` provides columns for localisation for trait data from the Biodiversity Exploratories sites (ww.biodiversity-exploratories.de). 


This list will also be available as 

- a csv/txt/xlsx table file which will be provided for download on BExIS including full documentation in the metadata (for manual use, this may be uploaded to BExIs as soon it's ready), and
- a machine readable template glossary (xml file or csv with additional flags and markers) which serves as input reference for software tools. (can we provide a simple API?) 


```
## Warning: package 'knitr' was built under R version 3.2.5
```

# Core traitdata columns

Generally, for the essential primary data (taxon assignment, trait name, trait value), the trait data standard recommends to keep the original naming and value of the data provider to ensure compatibility on the provider's side and to check for inconsistencies and misspellings. To ensure compatibility with other datasets, the original data provider's information should be transferred into a standardized columns indexed by appending `Std` to the column name. 
The R package 'traitdataform' helps in transferring those entries into the accepted taxon names and trait definitions provided by public ontologies. 

## `occurenceID`  

|             |occurenceID                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|defaultValue |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|valueType    |character                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|Identifier   |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|Refines      |http://rs.tdwg.org/dwc/terms/occurrenceID                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|Version      |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|Definition   |A character string user defined by the data author; a museum ID referring to the individual specimen from which the data were measured; usually does not apply for literature data.                                                                                                                                                                                                                                                                                               |
|Comment      |This is important for the analysis of co-variation of morphometric data or intraspecific variation. It may also couples multiple measurements on a single specimen, which also could be a leaf or a single bone without an assignment to an individual organism. If available, upload related dataset to describe specimens more precisely, e.g. environmental parameters or identity related information. May map to DWC OccurenceID (http://rs.tdwg.org/dwc/terms/occurrenceID) |
## `occurenceID_original`  

|             |occurenceID_original                                            |
|:------------|:---------------------------------------------------------------|
|mandatory    |TRUE                                                            |
|defaultValue |NA                                                              |
|vocabulary   |                                                                |
|valueType    |character                                                       |
|Identifier   |NA                                                              |
|Refines      |http://rs.tdwg.org/dwc/terms/occurrenceID                       |
|Replaces     |NA                                                              |
|Version      |NA                                                              |
|DateIssued   |NA                                                              |
|DateModified |NA                                                              |
|Definition   |Original user-defined identifier of the individual or specimen. |
|Comment      |Can be of any format.                                           |
## `scientificName`  

|             |scientificName                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|defaultValue |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|valueType    |character                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|Identifier   |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|Refines      |http://rs.tdwg.org/dwc/terms/scientificName                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|Version      |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|Definition   |Full scientific name (with authorship and date information if known). It should be an accepted taxon name according to a published taxonomy (provided in taxonID).                                                                                                                                                                                                                                                                                                                                                                                                                  |
|Comment      |Provide reference taxonomy in metadata of the dataset. Examples: "Coleoptera" (order), "Vespertilionidae" (family), "Manis" (genus), "Ctenomys sociabilis" (genus + specificEpithet), "Ambystoma tigrinum diaboli" (genus + specificEpithet + infraspecificEpithet), "Roptrocerus typographi (Györfi, 1952)" (genus + specificEpithet + scientificNameAuthorship), "Quercus agrifolia var. oxyadenia (Torr.) J.T. Howell" (genus + specificEpithet + taxonRank + infraspecificEpithet + scientificNameAuthorship). For discussion see http://terms.tdwg.org/wiki/dwc:scientificName |
## `scientificName_original`  

|             |scientificName_original                                                                                               |
|:------------|:---------------------------------------------------------------------------------------------------------------------|
|mandatory    |NA                                                                                                                    |
|defaultValue |                                                                                                                      |
|vocabulary   |                                                                                                                      |
|valueType    |character                                                                                                             |
|Identifier   |NA                                                                                                                    |
|Refines      |http://rs.tdwg.org/dwc/terms/scientificName                                                                           |
|Replaces     |NA                                                                                                                    |
|Version      |NA                                                                                                                    |
|DateIssued   |NA                                                                                                                    |
|DateModified |NA                                                                                                                    |
|Definition   |Original character string provided as species name by the data owner (kept for reference only)                        |
|Comment      |Can be equal to scientificName. Authors may use abbreviations, or use underscores to separate genus and species name. |
## `taxonID`  

|             |taxonID                                                                                                                                                                                                                            |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                              |
|defaultValue |NA                                                                                                                                                                                                                                 |
|vocabulary   |                                                                                                                                                                                                                                   |
|valueType    |factor                                                                                                                                                                                                                             |
|Identifier   |NA                                                                                                                                                                                                                                 |
|Refines      |http://rs.tdwg.org/dwc/terms/taxonID                                                                                                                                                                                               |
|Replaces     |NA                                                                                                                                                                                                                                 |
|Version      |NA                                                                                                                                                                                                                                 |
|DateIssued   |NA                                                                                                                                                                                                                                 |
|DateModified |NA                                                                                                                                                                                                                                 |
|Definition   |Verified name identifier  of the species or subspecies (or higher taxon) for which this value was collected. Each entry should linkt to a published reference species  list/taxonomy. Avoid synonyms.                              |
|Comment      |Examples: "GBIF Backbone Taxonomy:497924", "8fa58e08-08de-4ac1-b69c-1235340b7001", "32567", "http://species.gbif.org/abies_alba_1753", "urn:lsid:gbif.org:usages:32567". For discussion see http://terms.tdwg.org/wiki/dwc:taxonID |
## `taxonRank`  

|             |taxonRank                                                                                                                                                                                                                                                                                                                                                            |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                                                                                                                                |
|defaultValue |NA                                                                                                                                                                                                                                                                                                                                                                   |
|vocabulary   |domain; kingdom; subkingdom; superhpylum; phylum; subphylum; superclass; class; subclass; supercohort; cohort; subcohort; superorder; order; subordern; infraorder; superfamily; family; subfamily; tribe; subtribe; genus; subgenus; section; subsection; series; subseries; speciesAggregate; species; subspecificAggregate; subspecies; variety; cultivar; strain |
|valueType    |factor                                                                                                                                                                                                                                                                                                                                                               |
|Identifier   |NA                                                                                                                                                                                                                                                                                                                                                                   |
|Refines      |http://rs.tdwg.org/dwc/terms/taxonRank                                                                                                                                                                                                                                                                                                                               |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                                   |
|Version      |NA                                                                                                                                                                                                                                                                                                                                                                   |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                                                                                   |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                                   |
|Definition   |The taxonomic rank of the most specific name in the scientificName. Recommended best practice is to use a controlled vocabulary.                                                                                                                                                                                                                                     |
|Comment      |This is to clarify cases where information is not given on a species level. Examples: "subspecies", "varietas", "forma", "species", "genus".                                                                                                                                                                                                                         |
## `kingdom`  

|             |kingdom                                                                                    |
|:------------|:------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                      |
|defaultValue |NA                                                                                         |
|vocabulary   |                                                                                           |
|valueType    |factor                                                                                     |
|Identifier   |NA                                                                                         |
|Refines      |http://rs.tdwg.org/dwc/terms/kingdom                                                       |
|Replaces     |NA                                                                                         |
|Version      |NA                                                                                         |
|DateIssued   |NA                                                                                         |
|DateModified |NA                                                                                         |
|Definition   |The full scientific name of the kingdom in which the taxon is classified.                  |
|Comment      |Examples: "Animalia", "Plantae". For discussion see http://terms.tdwg.org/wiki/dwc:kingdom |
## `traitName_original`  

|             |traitName_original                                                                                                                                            |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |TRUE                                                                                                                                                          |
|defaultValue |NA                                                                                                                                                            |
|vocabulary   |                                                                                                                                                              |
|valueType    |character                                                                                                                                                     |
|Identifier   |NA                                                                                                                                                            |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementType                                                                                                                  |
|Replaces     |NA                                                                                                                                                            |
|Version      |NA                                                                                                                                                            |
|DateIssued   |NA                                                                                                                                                            |
|DateModified |NA                                                                                                                                                            |
|Definition   |Name of the trait as used by the data provider (kept for compatibility on provider side).                                                                     |
|Comment      |This can be a short name or user defined coded trait name. However, it is recommended to provide definition of the user provided trait names in the metadata. |
## `traitName`  

|             |traitName                                                                                                                                                           |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                               |
|defaultValue |NA                                                                                                                                                                  |
|vocabulary   |                                                                                                                                                                    |
|valueType    |factor                                                                                                                                                              |
|Identifier   |NA                                                                                                                                                                  |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementType                                                                                                                        |
|Replaces     |NA                                                                                                                                                                  |
|Version      |NA                                                                                                                                                                  |
|DateIssued   |NA                                                                                                                                                                  |
|DateModified |NA                                                                                                                                                                  |
|Definition   |Descriptive Name of the trait reported. This should follow the controlled vocabulary of a thesaurus of traits available online or published along with the dataset. |
|Comment      |Accompanying this, the traitID should provide an unambiguous link to the trait definition in the thesaurus or supplementary dataset.                                |
## `traitID`  

|             |traitID                                                                             |
|:------------|:-----------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                               |
|defaultValue |NA                                                                                  |
|vocabulary   |see traitlist                                                                       |
|valueType    |factor                                                                              |
|Identifier   |NA                                                                                  |
|Refines      |                                                                                    |
|Replaces     |NA                                                                                  |
|Version      |NA                                                                                  |
|DateIssued   |NA                                                                                  |
|DateModified |NA                                                                                  |
|Definition   |Unique identifier of the trait following the thesaurus of traits available on BExIS |
|Comment      |                                                                                    |
## `traitValue_original`  

|             |traitValue_original                                                                                                                                                                          |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |TRUE                                                                                                                                                                                         |
|defaultValue |NA                                                                                                                                                                                           |
|vocabulary   |                                                                                                                                                                                             |
|valueType    |character                                                                                                                                                                                    |
|Identifier   |NA                                                                                                                                                                                           |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementValue                                                                                                                                                |
|Replaces     |NA                                                                                                                                                                                           |
|Version      |NA                                                                                                                                                                                           |
|DateIssued   |NA                                                                                                                                                                                           |
|DateModified |NA                                                                                                                                                                                           |
|Definition   |Measured raw value or factor level for this species trait as measured and provided by the author.                                                                                            |
|Comment      |Must respect the unit given in 'measurementUnit_user' for numerical traits. For categorical traits, the factor levels should be harmonized across the dataset and explained in the metadata. |
## `traitUnit_original`  

|             |traitUnit_original                                                                                                                                                            |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |TRUE                                                                                                                                                                          |
|defaultValue |NA                                                                                                                                                                            |
|vocabulary   |                                                                                                                                                                              |
|valueType    |character                                                                                                                                                                     |
|Identifier   |NA                                                                                                                                                                            |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementUnit                                                                                                                                  |
|Replaces     |NA                                                                                                                                                                            |
|Version      |NA                                                                                                                                                                            |
|DateIssued   |NA                                                                                                                                                                            |
|DateModified |NA                                                                                                                                                                            |
|Definition   |Reports the unit that the author's raw data were measured in, if applicable (only for numeric values).                                                                        |
|Comment      |For numerical values report unit in format for lengths "mm", for volumes "mm3" / "mm^3", areas "mm2" / "mm^2", for movement "m/s", or for volume to surface ratios: "mm3/mm2" |
## `traitValue`  

|             |traitValue                                                                                                                                                                                            |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |TRUE                                                                                                                                                                                                  |
|defaultValue |NA                                                                                                                                                                                                    |
|vocabulary   |                                                                                                                                                                                                      |
|valueType    |character                                                                                                                                                                                             |
|Identifier   |NA                                                                                                                                                                                                    |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementValue                                                                                                                                                         |
|Replaces     |NA                                                                                                                                                                                                    |
|Version      |NA                                                                                                                                                                                                    |
|DateIssued   |NA                                                                                                                                                                                                    |
|DateModified |NA                                                                                                                                                                                                    |
|Definition   |Standardised measured value or factor level for this species trait. Numerical values must use the correct unit. Factor levels  must be compliant with the thesaurus of traits.                        |
|Comment      |Using "." as a decimal separator! The standardized data values or factor levels must correspond to the expected units and factor levels of the trait thesaurus, e.g. "32.423", "female", "apter", "3" |
## `traitUnit`  

|             |traitUnit                                                                                                                                                                       |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                           |
|defaultValue |NA                                                                                                                                                                              |
|vocabulary   |                                                                                                                                                                                |
|valueType    |character                                                                                                                                                                       |
|Identifier   |NA                                                                                                                                                                              |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementUnit                                                                                                                                    |
|Replaces     |NA                                                                                                                                                                              |
|Version      |NA                                                                                                                                                                              |
|DateIssued   |NA                                                                                                                                                                              |
|DateModified |NA                                                                                                                                                                              |
|Definition   |The units associated with the measurementValue. The expected standard unit for this trait as defined in the traitlist/ thesaurus.                                               |
|Comment      |Recommended best practice is to use the International System of Units (SI).  Examples: "mm", "C", "km", "ha". For discussion see http://terms.tdwg.org/wiki/dwc:measurementUnit |
## `measurementID`  

|             |measurementID                                                                                                                                                                                                                                                             |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                                     |
|defaultValue |NA                                                                                                                                                                                                                                                                        |
|vocabulary   |                                                                                                                                                                                                                                                                          |
|valueType    |character                                                                                                                                                                                                                                                                 |
|Identifier   |NA                                                                                                                                                                                                                                                                        |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementID                                                                                                                                                                                                                                |
|Replaces     |NA                                                                                                                                                                                                                                                                        |
|Version      |NA                                                                                                                                                                                                                                                                        |
|DateIssued   |NA                                                                                                                                                                                                                                                                        |
|DateModified |NA                                                                                                                                                                                                                                                                        |
|Definition   |An auto-generated unique identifier for each entry of data compiled as a MD5 hash from the following columns 'specimenID', 'measurementValue_user', 'scientificName_user', 'traitName_user', 'basisOfRecord', as well as the fields from class 'specimen' and 'location'. |
|Comment      |This allows a row-wise comparison of data from different versions and sources and an elimination of duplicates.                                                                                                                                                           |
## `measurementID_original`  

|             |measurementID_original                                                                                                                                                                                                                                                                                                                                                     |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                                                                                                                                      |
|defaultValue |NA                                                                                                                                                                                                                                                                                                                                                                         |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                                           |
|valueType    |character                                                                                                                                                                                                                                                                                                                                                                  |
|Identifier   |NA                                                                                                                                                                                                                                                                                                                                                                         |
|Refines      |                                                                                                                                                                                                                                                                                                                                                                           |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                                         |
|Version      |NA                                                                                                                                                                                                                                                                                                                                                                         |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                                                                                         |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                                         |
|Definition   |A unique, dataset-specific identifier. Links multi-value trait measurements, e.g. x-y-z coordinates of a morphometric landmark, biochemical compound quantities for different chainlengths. In this case, the trait names must specifiy the sub-measurement, e.g. "landmark32_x", and must be specified in a reference trait list, given in the field "measurementMethod". |
|Comment      |                                                                                                                                                                                                                                                                                                                                                                           |
## `warnings`  

|             |warnings                                                                                                                                                                                                                                                                                                              |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |NA                                                                                                                                                                                                                                                                                                                    |
|defaultValue |NA                                                                                                                                                                                                                                                                                                                    |
|vocabulary   |                                                                                                                                                                                                                                                                                                                      |
|valueType    |character                                                                                                                                                                                                                                                                                                             |
|Identifier   |NA                                                                                                                                                                                                                                                                                                                    |
|Refines      |                                                                                                                                                                                                                                                                                                                      |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                    |
|Version      |NA                                                                                                                                                                                                                                                                                                                    |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                                    |
|DateModified |NA                                                                                                                                                                                                                                                                                                                    |
|Definition   |warnings from the R-script will be stored here, e.g. ragarding a lack of match between the provided taxonID and the ontology, or the trait names or values, a mismatch in the units provided and the unit expected according to the trait table. User defined warnings and flags can be added as well, e.g. 'NOTUSE'. |
|Comment      |                                                                                                                                                                                                                                                                                                                      |


# Extension: Measurement or Fact 

This section provides additional information about the specimen, which are not captured by the taxon information above.  


## `references`  

|             |references                                                                                                                                                                                                                                                                                                            |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                                                                                 |
|defaultValue |NA                                                                                                                                                                                                                                                                                                                    |
|vocabulary   |                                                                                                                                                                                                                                                                                                                      |
|valueType    |character                                                                                                                                                                                                                                                                                                             |
|Identifier   |NA                                                                                                                                                                                                                                                                                                                    |
|Refines      |http://purl.org/dc/terms/references                                                                                                                                                                                                                                                                                   |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                    |
|Version      |NA                                                                                                                                                                                                                                                                                                                    |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                                    |
|DateModified |NA                                                                                                                                                                                                                                                                                                                    |
|Definition   |Precise reference to the source. If literature data, this should quote the book or online database. If museum this should report the name of the collection. If expert knowledge, this should name the authority. If trait database, provide reference to the original publication, DOI or URL of the trait-database. |
|Comment      |Examples: "http://mvzarctos.berkeley.edu/guid/MVZ:Mamm:165861"; "http://www.catalogueoflife.org/annual-checklist/show_species_details.php?record_id=6197868". For discussion see http://terms.tdwg.org/wiki/dwc:references                                                                                            |
## `measurementResolution`  

|             |measurementResolution                                                                                                                                                                                                                       |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                       |
|defaultValue |NA                                                                                                                                                                                                                                          |
|vocabulary   |                                                                                                                                                                                                                                            |
|valueType    |character                                                                                                                                                                                                                                   |
|Identifier   |NA                                                                                                                                                                                                                                          |
|Refines      |                                                                                                                                                                                                                                            |
|Replaces     |NA                                                                                                                                                                                                                                          |
|Version      |NA                                                                                                                                                                                                                                          |
|DateIssued   |NA                                                                                                                                                                                                                                          |
|DateModified |NA                                                                                                                                                                                                                                          |
|Definition   |If the trait information was originally given on another taxonomic level than species. Applies mainly for literature and expert knowledge data. not applying for measured data. The hierarchical level to which the trait data would refer. |
|Comment      |For example, information given in literature could state 'most species in this genus are winged', but the trait data could be given for each species in this genus.                                                                         |
## `preparations`  

|             |preparations                                                                                                                                                                                                                                                                                        |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                                                               |
|defaultValue |NA                                                                                                                                                                                                                                                                                                  |
|vocabulary   |                                                                                                                                                                                                                                                                                                    |
|valueType    |character                                                                                                                                                                                                                                                                                           |
|Identifier   |NA                                                                                                                                                                                                                                                                                                  |
|Refines      |http://rs.tdwg.org/dwc/terms/preparations                                                                                                                                                                                                                                                           |
|Replaces     |NA                                                                                                                                                                                                                                                                                                  |
|Version      |NA                                                                                                                                                                                                                                                                                                  |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                  |
|DateModified |NA                                                                                                                                                                                                                                                                                                  |
|Definition   |For preserved specimens, a list (concatenated and separated) of preparations and preservation methods for a specimen.                                                                                                                                                                               |
|Comment      |The recommended best practice is to separate the values with a vertical bar (' &#124; '). Examples: "fossil", "cast", "photograph", "DNA extract", "skin &#124; "skull &#124; skeleton", "whole animal (ETOH) &#124; tissue (EDTA)". For discussion see http://terms.tdwg.org/wiki/dwc:preparations |
## `measurementMethod`  

|             |measurementMethod                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|defaultValue |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|valueType    |character                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|Identifier   |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementMethod                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|Version      |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|Definition   |Applies primarily to measured data. The method, tools and scales used to measure a (numerical) trait value. A description of or reference to (publication, URI) the method or protocol used to determine the measurement, fact, characteristic, or assertion.                                                                                                                                                                                                                                                            |
|Comment      |Should be a concise and standardised text entry or reference (publication, URI), referring to a particular method (e.g. 'direct weighing', 'length-mass regression', 'intertegular span', 'length between node X and y' ) and  measurement conditions (e.g. certain temperature or humidity, name of device or scale used for measurement).  A more detailed description of the method or protocol used to determine the measurement, fact, characteristic, or assertion should be given in the metadata of the dataset. |
## `measurementDeterminedBy`  

|             |measurementDeterminedBy                                                                                                                                                                                                                                     |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                       |
|defaultValue |NA                                                                                                                                                                                                                                                          |
|vocabulary   |                                                                                                                                                                                                                                                            |
|valueType    |character                                                                                                                                                                                                                                                   |
|Identifier   |NA                                                                                                                                                                                                                                                          |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementDeterminedBy                                                                                                                                                                                                        |
|Replaces     |NA                                                                                                                                                                                                                                                          |
|Version      |NA                                                                                                                                                                                                                                                          |
|DateIssued   |NA                                                                                                                                                                                                                                                          |
|DateModified |NA                                                                                                                                                                                                                                                          |
|Definition   |A list (concatenated and separated) of names of people, groups, or organizations who determined the value of the measurement. Can be encoded by dataset-specific identifiers for reasons of privacy. This is kept as a co-factor for repeated measurements. |
|Comment      |The recommended best practice is to separate the values with a vertical bar (' &#124; '). Examples: "Rob Guralnick", "Julie Woodruff &#124; Eileen Lacey".                                                                                                  |
## `measurementDeterminedDate`  

|             |measurementDeterminedDate                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|defaultValue |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|valueType    |Date                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|Identifier   |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementDeterminedDate                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|Version      |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|Definition   |The date of the measurement. Also kept as a co-factor. Use format "YYYY-MM-DD hh:mm TIMEZONE". Not to confuse with year, month, day columns which are reserved for the date of sampling (may be identical, though).                                                                                                                                                                                                                                                                                  |
|Comment      |Examples: "1963-03-08T14:07-0600" is 8 Mar 1963 2:07pm in the time zone six hours earlier than UTC, "2009-02-20T08:40Z" is 20 Feb 2009 8:40am UTC, "1809-02-12" is 12 Feb 1809, "1906-06" is Jun 1906, "1971" is just that year, "2007-03-01T13:00:00Z/2008-05-11T15:30:00Z" is the interval between 1 Mar 2007 1pm UTC and 11 May 2008 3:30pm UTC, "2007-11-13/15" is the interval between 13 Nov 2007 and 15 Nov 2007. For discussion see http://terms.tdwg.org/wiki/dwc:measurementDeterminedDate |
## `measurementRemarks`  

|             |measurementRemarks                                                                                                                        |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                     |
|defaultValue |NA                                                                                                                                        |
|vocabulary   |                                                                                                                                          |
|valueType    |character                                                                                                                                 |
|Identifier   |NA                                                                                                                                        |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementRemarks                                                                                           |
|Replaces     |NA                                                                                                                                        |
|Version      |NA                                                                                                                                        |
|DateIssued   |NA                                                                                                                                        |
|DateModified |NA                                                                                                                                        |
|Definition   |Remarks concerning a particular measurement, e.g. additional information on the quality and reliability, reference or acknowledgements.   |
|Comment      |Any particularities about the individual measurement or specimen that might affect trait measuremnt, e.g. 'last antenna segment missing'. |
## `aggregateMeasure`  

|             |aggregateMeasure                                                                                                                                                                                                                                                                                               |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                                                                          |
|defaultValue |FALSE                                                                                                                                                                                                                                                                                                          |
|vocabulary   |                                                                                                                                                                                                                                                                                                               |
|valueType    |logical                                                                                                                                                                                                                                                                                                        |
|Identifier   |NA                                                                                                                                                                                                                                                                                                             |
|Refines      |                                                                                                                                                                                                                                                                                                               |
|Replaces     |NA                                                                                                                                                                                                                                                                                                             |
|Version      |NA                                                                                                                                                                                                                                                                                                             |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                             |
|DateModified |NA                                                                                                                                                                                                                                                                                                             |
|Definition   |Is measurementValue reporting an individual measurement or an aggregate Measure? TRUE or FALSE, defaults to FALSE.                                                                                                                                                                                             |
|Comment      |This is flagging aggregate data in an unambiguous way. Aggregate measures are often reported for repeated measures, e.g. replicate measurements of leaf size from a single plant individual or for grouped measurement, e.g. for weightings of a counted number of specimens (e.g. leaves or small organisms). |
## `individualCount`  

|             |individualCount                                                                                                                                      |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                |
|defaultValue |1                                                                                                                                                    |
|vocabulary   |                                                                                                                                                     |
|valueType    |integer                                                                                                                                              |
|Identifier   |NA                                                                                                                                                   |
|Refines      |http://rs.tdwg.org/dwc/terms/individualCount                                                                                                         |
|Replaces     |NA                                                                                                                                                   |
|Version      |NA                                                                                                                                                   |
|DateIssued   |NA                                                                                                                                                   |
|DateModified |NA                                                                                                                                                   |
|Definition   |If measurement is an aggregate measure of multiple individuals or specimens, report number of specimens as count, i.e. integer number. Defaults to 1 |
|Comment      |Examples: "1", "25". For discussion see http://terms.tdwg.org/wiki/dwc:individualCount                                                               |
## `dispersion`  

|             |dispersion                                                                                                                                                                                                                                                                                                                                |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                                                                                                     |
|defaultValue |0                                                                                                                                                                                                                                                                                                                                         |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                          |
|valueType    |numeric                                                                                                                                                                                                                                                                                                                                   |
|Identifier   |NA                                                                                                                                                                                                                                                                                                                                        |
|Refines      |                                                                                                                                                                                                                                                                                                                                          |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                        |
|Version      |NA                                                                                                                                                                                                                                                                                                                                        |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                                                        |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                        |
|Definition   |If aggregate measure of multiple individuals or specimens, the numeric value of dispersion (variance or standard deviation) for the mean value reported in measurementValue_user (no unit conversion is provided by the R-package!). Defaults to 0. If a value is provided, report the statistical method in the field statisticalMethod. |
|Comment      |                                                                                                                                                                                                                                                                                                                                          |
## `measurementValue_min`  

|             |measurementValue_min                                                                   |
|:------------|:--------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                  |
|defaultValue |NA                                                                                     |
|vocabulary   |                                                                                       |
|valueType    |numeric                                                                                |
|Identifier   |NA                                                                                     |
|Refines      |                                                                                       |
|Replaces     |NA                                                                                     |
|Version      |NA                                                                                     |
|DateIssued   |NA                                                                                     |
|DateModified |NA                                                                                     |
|Definition   |The lower boundary of observed values. Instead of or in addition to dispersion metric. |
|Comment      |                                                                                       |
## `measurementValue_max`  

|             |measurementValue_max                                                                   |
|:------------|:--------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                  |
|defaultValue |NA                                                                                     |
|vocabulary   |                                                                                       |
|valueType    |numeric                                                                                |
|Identifier   |NA                                                                                     |
|Refines      |                                                                                       |
|Replaces     |NA                                                                                     |
|Version      |NA                                                                                     |
|DateIssued   |NA                                                                                     |
|DateModified |NA                                                                                     |
|Definition   |The upper boundary of observed values. Instead of or in addition to dispersion metric. |
|Comment      |                                                                                       |
## `measurementAccuracy`  

|             |measurementAccuracy                                                                                                                  |
|:------------|:------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                |
|defaultValue |NA                                                                                                                                   |
|vocabulary   |                                                                                                                                     |
|valueType    |character                                                                                                                            |
|Identifier   |NA                                                                                                                                   |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementAccuracy                                                                                     |
|Replaces     |NA                                                                                                                                   |
|Version      |NA                                                                                                                                   |
|DateIssued   |NA                                                                                                                                   |
|DateModified |NA                                                                                                                                   |
|Definition   |The description of the potential error associated with the measurementValue.                                                         |
|Comment      |Examples: "0.01", "normal distribution with variation of 2 m". For discussion see http://terms.tdwg.org/wiki/dwc:measurementAccuracy |
## `statisticalMethod`  

|             |statisticalMethod                                                                                                                                               |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                           |
|defaultValue |NA                                                                                                                                                              |
|vocabulary   |                                                                                                                                                                |
|valueType    |character                                                                                                                                                       |
|Identifier   |NA                                                                                                                                                              |
|Refines      |                                                                                                                                                                |
|Replaces     |NA                                                                                                                                                              |
|Version      |NA                                                                                                                                                              |
|DateIssued   |NA                                                                                                                                                              |
|DateModified |NA                                                                                                                                                              |
|Definition   |For aggregated measures, the method for data aggregation or averaging as well as the variation or range.                                                        |
|Comment      |E.g. 'mean and standard deviation', 'median and 95% confidence interval', 'mean and variance', 'mean and range of values', 'median and 95% interquantile range' |


# Extension: Occurence 

this section of columns aims for identifying the methodology and primary source of the data and keep the reference to the actual specimen (e.g. for museum collections or related data analysis). 

## `basisOfRecord`  

|             |basisOfRecord                                                                                                                                                                                                                                                                                         |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |TRUE                                                                                                                                                                                                                                                                                                  |
|defaultValue |NA                                                                                                                                                                                                                                                                                                    |
|vocabulary   |LivingSpecimen; PreservedSpecimen; FossilSpecimen; literatureData; traitDatabase; expertKnowledge                                                                                                                                                                                                     |
|valueType    |factor                                                                                                                                                                                                                                                                                                |
|Identifier   |NA                                                                                                                                                                                                                                                                                                    |
|Refines      |http://rs.tdwg.org/dwc/terms/basisOfRecord                                                                                                                                                                                                                                                            |
|Replaces     |NA                                                                                                                                                                                                                                                                                                    |
|Version      |NA                                                                                                                                                                                                                                                                                                    |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                    |
|DateModified |NA                                                                                                                                                                                                                                                                                                    |
|Definition   |How and from which kind of speciment were the data obtained? Options are: Taken by own measurement (distinguish LivingSpecimen, PreservedSpecimen, FossilSpecimen) or taken from literature (literatureData), from an existing trait database (traitDatabase), or expert knowledge (expertKnowledge). |
|Comment      |                                                                                                                                                                                                                                                                                                      |
## `basisOfRecordDescription`  

|             |basisOfRecordDescription                                                                                                                                                                                                                                                              |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                                                 |
|defaultValue |NA                                                                                                                                                                                                                                                                                    |
|vocabulary   |                                                                                                                                                                                                                                                                                      |
|valueType    |character                                                                                                                                                                                                                                                                             |
|Identifier   |NA                                                                                                                                                                                                                                                                                    |
|Refines      |                                                                                                                                                                                                                                                                                      |
|Replaces     |NA                                                                                                                                                                                                                                                                                    |
|Version      |NA                                                                                                                                                                                                                                                                                    |
|DateIssued   |NA                                                                                                                                                                                                                                                                                    |
|DateModified |NA                                                                                                                                                                                                                                                                                    |
|Definition   |Adding more detail to the basisOfRecord. If life specimens were sampled, where did they come from? Have they been reared in cultivation? If literature data, provide type of literature, e.g. textbook, website, database, etc. If preserved specimens were used, which method of pre |
|Comment      |                                                                                                                                                                                                                                                                                      |
## `sex`  

|             |sex                                                                                                                                                         |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                       |
|defaultValue |NA                                                                                                                                                          |
|vocabulary   |male; female; subadult; unknown; hermaphrodite                                                                                                              |
|valueType    |factor                                                                                                                                                      |
|Identifier   |NA                                                                                                                                                          |
|Refines      |http://rs.tdwg.org/dwc/terms/sex                                                                                                                            |
|Replaces     |NA                                                                                                                                                          |
|Version      |NA                                                                                                                                                          |
|DateIssued   |NA                                                                                                                                                          |
|DateModified |NA                                                                                                                                                          |
|Definition   |Defining the sex of the measured specimen, to capture dimorphisms. Standardised factor levels are: "male", "female", "subadult", "unknown", "hermaphrodite" |
|Comment      |                                                                                                                                                            |
## `lifeStage`  

|             |lifeStage                                                                                                                                                                                                                                                  |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                      |
|defaultValue |NA                                                                                                                                                                                                                                                         |
|vocabulary   |                                                                                                                                                                                                                                                           |
|valueType    |character                                                                                                                                                                                                                                                  |
|Identifier   |NA                                                                                                                                                                                                                                                         |
|Refines      |http://rs.tdwg.org/dwc/terms/lifeStage                                                                                                                                                                                                                     |
|Replaces     |NA                                                                                                                                                                                                                                                         |
|Version      |NA                                                                                                                                                                                                                                                         |
|DateIssued   |NA                                                                                                                                                                                                                                                         |
|DateModified |NA                                                                                                                                                                                                                                                         |
|Definition   |The life stage of the measured specimen.                                                                                                                                                                                                                   |
|Comment      |Recommended factor levels are: seed, seedling, sapling, adult, egg, larval_instar_1, larval_instar_2, larval_instar_3, ... , pupa; For very taxon-specific life stages, it is recommended to provide detailled explanation in the metadata of the dataset. |
## `age`  

|             |age                               |
|:------------|:---------------------------------|
|mandatory    |FALSE                             |
|defaultValue |NA                                |
|vocabulary   |                                  |
|valueType    |numeric                           |
|Identifier   |NA                                |
|Refines      |                                  |
|Replaces     |NA                                |
|Version      |NA                                |
|DateIssued   |NA                                |
|DateModified |NA                                |
|Definition   |The age of the specimen in years. |
|Comment      |Example: "2", "0.16".             |
## `morphotype`  

|             |morphotype                                                                                                                                                    |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                         |
|defaultValue |NA                                                                                                                                                            |
|vocabulary   |                                                                                                                                                              |
|valueType    |character                                                                                                                                                     |
|Identifier   |NA                                                                                                                                                            |
|Refines      |                                                                                                                                                              |
|Replaces     |NA                                                                                                                                                            |
|Version      |NA                                                                                                                                                            |
|DateIssued   |NA                                                                                                                                                            |
|DateModified |NA                                                                                                                                                            |
|Definition   |The morphotype of the observed specimen.                                                                                                                      |
|Comment      |Examples: "worker", "drone", "queen". Since morphotypes can differ between organism groups, provide definition of morphotypes in the metadata of the dataset. |
## `eventID`  

|             |eventID                                                                                                                                                                                                                                                         |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                           |
|defaultValue |NA                                                                                                                                                                                                                                                              |
|vocabulary   |                                                                                                                                                                                                                                                                |
|valueType    |character                                                                                                                                                                                                                                                       |
|Identifier   |NA                                                                                                                                                                                                                                                              |
|Refines      |                                                                                                                                                                                                                                                                |
|Replaces     |NA                                                                                                                                                                                                                                                              |
|Version      |NA                                                                                                                                                                                                                                                              |
|DateIssued   |NA                                                                                                                                                                                                                                                              |
|DateModified |NA                                                                                                                                                                                                                                                              |
|Definition   |The sampling event or campaign. User specified character string. could link to another table that provides more information, e.g. environmental or temporal parameters, descriptions on methods etc.. should link to official Exploratories sampling campaigns. |
|Comment      |                                                                                                                                                                                                                                                                |
## `samplingProtocol`  

|             |samplingProtocol                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|defaultValue |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|valueType    |character                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|Identifier   |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|Refines      |http://rs.tdwg.org/dwc/terms/samplingProtocol                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|Version      |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|Definition   |The name of, reference to, or description of the method or protocol used for obtaining the specimen.                                                                                                                                                                                                                                                                                                                                                                                                                |
|Comment      |Examples: "UV light trap", "mist net", "bottom trawl", "ad hoc observation", "point count", "Penguins from space: faecal stains reveal the location of emperor penguin colonies, http://dx.doi.org/10.1111/j.1466-8238.2009.00467.x", "Takats et al. 2001. Guidelines for Nocturnal Owl Monitoring in North America. Beaverhill Bird Observatory and Bird Studies Canada, Edmonton, Alberta. 32 pp.", "http://www.bsc-eoc.org/download/Owl.pdf". For discussion see http://terms.tdwg.org/wiki/dwc:samplingProtocol |
## `year`  

|             |year                                                                    |
|:------------|:-----------------------------------------------------------------------|
|mandatory    |FALSE                                                                   |
|defaultValue |NA                                                                      |
|vocabulary   |                                                                        |
|valueType    |integer                                                                 |
|Identifier   |NA                                                                      |
|Refines      |http://rs.tdwg.org/dwc/terms/year                                       |
|Replaces     |NA                                                                      |
|Version      |NA                                                                      |
|DateIssued   |NA                                                                      |
|DateModified |NA                                                                      |
|Definition   |The four-digit year, at which the specimens were extracted or sampled.  |
|Comment      |Example: "2008". For discussion see http://terms.tdwg.org/wiki/dwc:year |
## `month`  

|             |month                                                                                              |
|:------------|:--------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                              |
|defaultValue |NA                                                                                                 |
|vocabulary   |                                                                                                   |
|valueType    |integer                                                                                            |
|Identifier   |NA                                                                                                 |
|Refines      |http://rs.tdwg.org/dwc/terms/month                                                                 |
|Replaces     |NA                                                                                                 |
|Version      |NA                                                                                                 |
|DateIssued   |NA                                                                                                 |
|DateModified |NA                                                                                                 |
|Definition   |The ordinal month, in which the specimens were extracted or sampled.                               |
|Comment      |Examples: "1" (=January), "10" (=October). For discussion see http://terms.tdwg.org/wiki/dwc:month |
## `day`  

|             |day                                                                            |
|:------------|:------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                          |
|defaultValue |NA                                                                             |
|vocabulary   |                                                                               |
|valueType    |integer                                                                        |
|Identifier   |NA                                                                             |
|Refines      |http://rs.tdwg.org/dwc/terms/day                                               |
|Replaces     |NA                                                                             |
|Version      |NA                                                                             |
|DateIssued   |NA                                                                             |
|DateModified |NA                                                                             |
|Definition   |The integer day of the month on which the specimens were extracted or sampled. |
|Comment      |Examples: "9", "28". For discussion see http://terms.tdwg.org/wiki/dwc:day     |
## `eventDate`  

|             |eventDate                                                                                                                                                                                                                                                                                                                                    |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                                                                                                        |
|defaultValue |NA                                                                                                                                                                                                                                                                                                                                           |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                             |
|valueType    |Date                                                                                                                                                                                                                                                                                                                                         |
|Identifier   |NA                                                                                                                                                                                                                                                                                                                                           |
|Refines      |http://rs.tdwg.org/dwc/terms/eventDate                                                                                                                                                                                                                                                                                                       |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                           |
|Version      |NA                                                                                                                                                                                                                                                                                                                                           |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                                                           |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                           |
|Definition   |Represents the date, at which the specimens were extracted or sampled. If providing eventDate, then enter format of type: YYYY-MM-DD hh:mm TIMEZONE (fall back to 12:00 if no time is available).                                                                                                                                            |
|Comment      |For lower precision, use year, month and day field instead. Note: this is not to record the date when the specimens were measured (use measurementDeterminedDate for this). If applicable, at least provide a year. This is particularly important if the measurements were taken from specimens from the exploratories or museum specimens. |
## `locationID`  

|             |locationID                                                                                                                                                                                                                             |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                  |
|defaultValue |NA                                                                                                                                                                                                                                     |
|vocabulary   |                                                                                                                                                                                                                                       |
|valueType    |factor                                                                                                                                                                                                                                 |
|Identifier   |NA                                                                                                                                                                                                                                     |
|Refines      |http://rs.tdwg.org/dwc/terms/locationID                                                                                                                                                                                                |
|Replaces     |NA                                                                                                                                                                                                                                     |
|Version      |NA                                                                                                                                                                                                                                     |
|DateIssued   |NA                                                                                                                                                                                                                                     |
|DateModified |NA                                                                                                                                                                                                                                     |
|Definition   |A unique, dataset-specific identifier. Could report the subplot within the Exploratories, or the plot or replicate of a separate experimental setting. If further information is available, specify locationIDs in a separate dataset. |
|Comment      |                                                                                                                                                                                                                                       |
## `habitat`  

|             |habitat                                                                                                                                             |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                               |
|defaultValue |NA                                                                                                                                                  |
|vocabulary   |                                                                                                                                                    |
|valueType    |factor                                                                                                                                              |
|Identifier   |NA                                                                                                                                                  |
|Refines      |http://rs.tdwg.org/dwc/terms/habitat                                                                                                                |
|Replaces     |NA                                                                                                                                                  |
|Version      |NA                                                                                                                                                  |
|DateIssued   |NA                                                                                                                                                  |
|DateModified |NA                                                                                                                                                  |
|Definition   |A character string reporting habitat type from which the specimen was sampled. E.g. 'forest', 'grassland', 'oak savanna', 'pre-cordilleran steppe'. |
|Comment      |                                                                                                                                                    |
## `decimalLongitude`  

|             |decimalLongitude                                                                                                                                                                                                                  |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                             |
|defaultValue |NA                                                                                                                                                                                                                                |
|vocabulary   |                                                                                                                                                                                                                                  |
|valueType    |numeric                                                                                                                                                                                                                           |
|Identifier   |NA                                                                                                                                                                                                                                |
|Refines      |http://rs.tdwg.org/dwc/terms/decimalLongitude                                                                                                                                                                                     |
|Replaces     |NA                                                                                                                                                                                                                                |
|Version      |NA                                                                                                                                                                                                                                |
|DateIssued   |NA                                                                                                                                                                                                                                |
|DateModified |NA                                                                                                                                                                                                                                |
|Definition   |The geographic longitude (in decimal degrees, using the spatial reference system given in geodeticDatum) of the geographic center of a Location.                                                                                  |
|Comment      |Positive values are east of the Greenwich Meridian, negative values are west of it. Legal values lie between -180 and 180, inclusive. Example: "-121.1761111". For discussion see http://terms.tdwg.org/wiki/dwc:decimalLongitude |
## `decimalLatitude`  

|             |decimalLatitude                                                                                                                                                                                                    |
|:------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                              |
|defaultValue |NA                                                                                                                                                                                                                 |
|vocabulary   |                                                                                                                                                                                                                   |
|valueType    |numeric                                                                                                                                                                                                            |
|Identifier   |NA                                                                                                                                                                                                                 |
|Refines      |http://rs.tdwg.org/dwc/terms/decimalLatitude                                                                                                                                                                       |
|Replaces     |NA                                                                                                                                                                                                                 |
|Version      |NA                                                                                                                                                                                                                 |
|DateIssued   |NA                                                                                                                                                                                                                 |
|DateModified |NA                                                                                                                                                                                                                 |
|Definition   |The geographic latitude (in decimal degrees, using the spatial reference system given in geodeticDatum) of the geographic center of a Location.                                                                    |
|Comment      |Positive values are north of Equator, negative values are south of it. Legal values lie between -180 and 180, inclusive. Example: "-41.0983423". For discussion see http://terms.tdwg.org/wiki/dwc:decimalLatitude |
## `elevation`  

|             |elevation                                                                                                                                                                                                                                                                                                                                          |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                                                                                                              |
|defaultValue |NA                                                                                                                                                                                                                                                                                                                                                 |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                   |
|valueType    |numeric                                                                                                                                                                                                                                                                                                                                            |
|Identifier   |NA                                                                                                                                                                                                                                                                                                                                                 |
|Refines      |                                                                                                                                                                                                                                                                                                                                                   |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                 |
|Version      |NA                                                                                                                                                                                                                                                                                                                                                 |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                                                                 |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                 |
|Definition   |The geographic elevation in meters above sea level.                                                                                                                                                                                                                                                                                                |
|Comment      |May map to verbatimElevation (http://rs.tdwg.org/dwc/terms/verbatimElevation) or minimumElevationInMeters (http://rs.tdwg.org/dwc/terms/minimumElevationInMeters) and maximumElevationInMeters (http://rs.tdwg.org/dwc/terms/maximumElevationInMeters); Example: "200". For discussion see http://terms.tdwg.org/wiki/dwc:maximumElevationInMeters |
## `geodeticDatum`  

|             |geodeticDatum                                                                                                                                                                                                                                                                                                                                            |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                                                                                                                    |
|defaultValue |NA                                                                                                                                                                                                                                                                                                                                                       |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                         |
|valueType    |factor                                                                                                                                                                                                                                                                                                                                                   |
|Identifier   |NA                                                                                                                                                                                                                                                                                                                                                       |
|Refines      |http://rs.tdwg.org/dwc/terms/geodeticDatum                                                                                                                                                                                                                                                                                                               |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                       |
|Version      |NA                                                                                                                                                                                                                                                                                                                                                       |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                                                                       |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                       |
|Definition   |The geodeticDatum defines the ellipsoid, geodetic datum, or spatial reference system (SRS) upon which the geographic coordinates given in decimalLatitude and decimalLongitude as based. Recommended system is "WGS84". Use the EPSG code to provide an SRS. Examples: "EPSG:4326", "WGS84", "NAD27", "Campo Inchauspe", "European 1950", "Clarke 1866"* |
|Comment      |                                                                                                                                                                                                                                                                                                                                                         |
## `verbatimLocality`  

|             |verbatimLocality                                                                                                                                                                                                                                                                                                                                           |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                                                                                                                      |
|defaultValue |NA                                                                                                                                                                                                                                                                                                                                                         |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                           |
|valueType    |character                                                                                                                                                                                                                                                                                                                                                  |
|Identifier   |NA                                                                                                                                                                                                                                                                                                                                                         |
|Refines      |http://rs.tdwg.org/dwc/terms/verbatimLocality                                                                                                                                                                                                                                                                                                              |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                         |
|Version      |NA                                                                                                                                                                                                                                                                                                                                                         |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                                                                         |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                         |
|Definition   |The specific description of the place. Less specific geographic information can be provided in other geographic terms (higherGeography, continent, country, stateProvince, county, municipality, waterBody, island, islandGroup). This term may contain information modified from the original to correct perceived errors or standardize the description. |
|Comment      |                                                                                                                                                                                                                                                                                                                                                           |
## `country`  

|             |country                                                                                                                                                                                                              |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                |
|defaultValue |NA                                                                                                                                                                                                                   |
|vocabulary   |                                                                                                                                                                                                                     |
|valueType    |character                                                                                                                                                                                                            |
|Identifier   |NA                                                                                                                                                                                                                   |
|Refines      |http://rs.tdwg.org/dwc/terms/country                                                                                                                                                                                 |
|Replaces     |NA                                                                                                                                                                                                                   |
|Version      |NA                                                                                                                                                                                                                   |
|DateIssued   |NA                                                                                                                                                                                                                   |
|DateModified |NA                                                                                                                                                                                                                   |
|Definition   |Recommended best practice is to use a controlled vocabulary such as the Getty Thesaurus of Geographic Names.                                                                                                         |
|Comment      |Examples: "Germany", "Denmark", "Colombia", "España". For discussion see http://terms.tdwg.org/wiki/dwc:country;  This should be added if a more precise location is unavailable, to enable data to be used by GBif. |
## `countryCode`  

|             |countryCode                                                                                                                                                                                                                            |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                  |
|defaultValue |NA                                                                                                                                                                                                                                     |
|vocabulary   |                                                                                                                                                                                                                                       |
|valueType    |factor                                                                                                                                                                                                                                 |
|Identifier   |NA                                                                                                                                                                                                                                     |
|Refines      |http://rs.tdwg.org/dwc/terms/countryCode                                                                                                                                                                                               |
|Replaces     |NA                                                                                                                                                                                                                                     |
|Version      |NA                                                                                                                                                                                                                                     |
|DateIssued   |NA                                                                                                                                                                                                                                     |
|DateModified |NA                                                                                                                                                                                                                                     |
|Definition   |The standard code for the country in which the Location occurs. Recommended best practice is to use ISO 3166-1-alpha-2 country codes.                                                                                                  |
|Comment      |Examples:"DE" for Germany, "AR" for Argentina, "SV" for El Salvador. For discussion see http://terms.tdwg.org/wiki/dwc:countryCode; This should be added if a more precise location is unavailable, to enable data to be used by GBif. |

# Extension: Biodiversity Exploratories

This section records location in the context of the exploratories. From `ExploratotriesPlotID` a detailled georeference can be inferred. Additional spatial resolution, e.g. on subplots, may be provided in `locationID` of section sampling event. 

## `OriginExploratories`  

|             |OriginExploratories                                                                         |
|:------------|:-------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                       |
|defaultValue |FALSE                                                                                       |
|vocabulary   |TRUE;FALSE                                                                                  |
|valueType    |logical                                                                                     |
|Identifier   |NA                                                                                          |
|Refines      |                                                                                            |
|Replaces     |NA                                                                                          |
|Version      |NA                                                                                          |
|DateIssued   |NA                                                                                          |
|DateModified |NA                                                                                          |
|Definition   |Did measured specimens originate from Exploratories Plots? TRUE or FALSE, defaults to FALSE |
|Comment      |As unambiguous flag for data and specimens that are originating from Exploratories sites.   |
## `ExploratoriesPlotID`  

|             |ExploratoriesPlotID                                                                                                                                                                                                                                                                                                                              |
|:------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                                                                                                                                                                                                            |
|defaultValue |NA                                                                                                                                                                                                                                                                                                                                               |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                 |
|valueType    |factor                                                                                                                                                                                                                                                                                                                                           |
|Identifier   |NA                                                                                                                                                                                                                                                                                                                                               |
|Refines      |                                                                                                                                                                                                                                                                                                                                                 |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                               |
|Version      |NA                                                                                                                                                                                                                                                                                                                                               |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                                                               |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                               |
|Definition   |EP plot ID (or also any valid Gridplot ID or VIP ID) where the measured specimen was extracted. Only for specimen that were extracted from the exploratories directly (or direct offspring, if hatched in the lab). Please also report it, even if this was not part of your research question and provide a Date (a year at last) if available. |
|Comment      |                                                                                                                                                                                                                                                                                                                                                 |
## `Exploratory`  

|             |Exploratory                                                                                                                                                       |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                                                             |
|defaultValue |NA                                                                                                                                                                |
|vocabulary   |H;S;A                                                                                                                                                             |
|valueType    |factor                                                                                                                                                            |
|Identifier   |NA                                                                                                                                                                |
|Refines      |                                                                                                                                                                  |
|Replaces     |NA                                                                                                                                                                |
|Version      |NA                                                                                                                                                                |
|DateIssued   |NA                                                                                                                                                                |
|DateModified |NA                                                                                                                                                                |
|Definition   |Exploratories Region (Hainich, Schorfheide, Alb) for sorting purpose and readability, or if exact Plot ID is not available. Report the Region in format: A, H, S. |
|Comment      |                                                                                                                                                                  |
## `ExploType`  

|             |ExploType                                                                                                                   |
|:------------|:---------------------------------------------------------------------------------------------------------------------------|
|mandatory    |FALSE                                                                                                                       |
|defaultValue |NA                                                                                                                          |
|vocabulary   |W; G                                                                                                                        |
|valueType    |factor                                                                                                                      |
|Identifier   |NA                                                                                                                          |
|Refines      |                                                                                                                            |
|Replaces     |NA                                                                                                                          |
|Version      |NA                                                                                                                          |
|DateIssued   |NA                                                                                                                          |
|DateModified |NA                                                                                                                          |
|Definition   |W for forest or G for grassland plot. This is automaticall extracted by the R script from ExploratoriesPlotID, if provided. |
|Comment      |                                                                                                                            |

# Metadata vocabulary

## `rightsHolder`  

|             |rightsHolder                                                                             |
|:------------|:----------------------------------------------------------------------------------------|
|mandatory    |NA                                                                                       |
|defaultValue |NA                                                                                       |
|vocabulary   |                                                                                         |
|valueType    |character                                                                                |
|Identifier   |NA                                                                                       |
|Refines      |http://purl.org/dc/terms/rightsHolder                                                    |
|Replaces     |NA                                                                                       |
|Version      |NA                                                                                       |
|DateIssued   |NA                                                                                       |
|DateModified |NA                                                                                       |
|Definition   |A person or organization owning or managing rights over the resource, i.e. this dataset. |
|Comment      |A list of author names (separated by &#124;) or name of a consortium, or institution     |
## `bibliographicCitation`  

|             |bibliographicCitation                                                                                                                                                                                                                                                                                            |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |NA                                                                                                                                                                                                                                                                                                               |
|defaultValue |NA                                                                                                                                                                                                                                                                                                               |
|vocabulary   |                                                                                                                                                                                                                                                                                                                 |
|valueType    |character                                                                                                                                                                                                                                                                                                        |
|Identifier   |NA                                                                                                                                                                                                                                                                                                               |
|Refines      |http://purl.org/dc/terms/bibliographicCitation                                                                                                                                                                                                                                                                   |
|Replaces     |NA                                                                                                                                                                                                                                                                                                               |
|Version      |NA                                                                                                                                                                                                                                                                                                               |
|DateIssued   |NA                                                                                                                                                                                                                                                                                                               |
|DateModified |NA                                                                                                                                                                                                                                                                                                               |
|Definition   |A bibliographic reference for the resource as a statement indicating how this record should be cited (attributed) when used. Recommended practice is to include sufficient bibliographic detail to identify the resource as unambiguously as possible.                                                           |
|Comment      |e.g. "Gossner, M.M., Simons, N.K., Achtziger, R., Blick, T., Dorow, W.H.., Dziock, F., et al. (2015). A summary of eight traits of Coleoptera, Hemiptera, Orthoptera and Araneae, occurring in grasslands in Germany. Sci Data, 2, 150013, doi:10.1038/sdata.2015.13" If dataset has been published, include DOI |
## `license`  

|             |license                                                                                                                                                                                   |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |NA                                                                                                                                                                                        |
|defaultValue |NA                                                                                                                                                                                        |
|vocabulary   |                                                                                                                                                                                          |
|valueType    |character                                                                                                                                                                                 |
|Identifier   |NA                                                                                                                                                                                        |
|Refines      |http://purl.org/dc/terms/license                                                                                                                                                          |
|Replaces     |NA                                                                                                                                                                                        |
|Version      |NA                                                                                                                                                                                        |
|DateIssued   |NA                                                                                                                                                                                        |
|DateModified |NA                                                                                                                                                                                        |
|Definition   |A legal document giving official permission to do something with the resource.                                                                                                            |
|Comment      |Examples: "http://creativecommons.org/publicdomain/zero/1.0/legalcode", "http://creativecommons.org/licenses/by/4.0/legalcode". For discussion see http://terms.tdwg.org/wiki/dwc:license |
## `datasetID`  

|             |datasetID                                                                                                                      |
|:------------|:------------------------------------------------------------------------------------------------------------------------------|
|mandatory    |NA                                                                                                                             |
|defaultValue |NA                                                                                                                             |
|vocabulary   |                                                                                                                               |
|valueType    |character                                                                                                                      |
|Identifier   |NA                                                                                                                             |
|Refines      |http://rs.tdwg.org/dwc/terms/datasetID                                                                                         |
|Replaces     |NA                                                                                                                             |
|Version      |NA                                                                                                                             |
|DateIssued   |NA                                                                                                                             |
|DateModified |NA                                                                                                                             |
|Definition   |An identifier for the set of data. May be a global unique identifier or an identifier specific to a collection or institution. |
|Comment      |e.g. BExIS ID, or  a DOI referring to the published dataset                                                                    |
## `datasetName`  

|             |datasetName                                                          |
|:------------|:--------------------------------------------------------------------|
|mandatory    |NA                                                                   |
|defaultValue |NA                                                                   |
|vocabulary   |                                                                     |
|valueType    |character                                                            |
|Identifier   |NA                                                                   |
|Refines      |http://rs.tdwg.org/dwc/terms/datasetName                             |
|Replaces     |NA                                                                   |
|Version      |NA                                                                   |
|DateIssued   |NA                                                                   |
|DateModified |NA                                                                   |
|Definition   |The name identifying the data set from which the record was derived. |
|Comment      |e.g. a BExIS dataset name, a unique name for the traitdataset        |

# Terms for Traitlists / Trait Thesaurus

## `valueType`  

|             |valueType |
|:------------|:---------|
|mandatory    |NA        |
|defaultValue |          |
|vocabulary   |          |
|valueType    |          |
|Identifier   |NA        |
|Refines      |          |
|Replaces     |NA        |
|Version      |NA        |
|DateIssued   |NA        |
|DateModified |NA        |
|Definition   |          |
|Comment      |          |
## `FactorLevels`  

|             |FactorLevels |
|:------------|:------------|
|mandatory    |NA           |
|defaultValue |             |
|vocabulary   |             |
|valueType    |             |
|Identifier   |NA           |
|Refines      |             |
|Replaces     |NA           |
|Version      |NA           |
|DateIssued   |NA           |
|DateModified |NA           |
|Definition   |             |
|Comment      |             |
## `MaxAllowedValue`  

|             |MaxAllowedValue |
|:------------|:---------------|
|mandatory    |NA              |
|defaultValue |                |
|vocabulary   |                |
|valueType    |                |
|Identifier   |NA              |
|Refines      |                |
|Replaces     |NA              |
|Version      |NA              |
|DateIssued   |NA              |
|DateModified |NA              |
|Definition   |                |
|Comment      |                |
## `MinAllowedValue`  

|             |MinAllowedValue |
|:------------|:---------------|
|mandatory    |NA              |
|defaultValue |                |
|vocabulary   |                |
|valueType    |                |
|Identifier   |NA              |
|Refines      |                |
|Replaces     |NA              |
|Version      |NA              |
|DateIssued   |NA              |
|DateModified |NA              |
|Definition   |                |
|Comment      |                |
## `MeasurementTypeDescription`  

|             |MeasurementTypeDescription |
|:------------|:--------------------------|
|mandatory    |NA                         |
|defaultValue |                           |
|vocabulary   |                           |
|valueType    |                           |
|Identifier   |NA                         |
|Refines      |                           |
|Replaces     |NA                         |
|Version      |NA                         |
|DateIssued   |NA                         |
|DateModified |NA                         |
|Definition   |                           |
|Comment      |                           |
## `Comments`  

|             |Comments |
|:------------|:--------|
|mandatory    |NA       |
|defaultValue |         |
|vocabulary   |         |
|valueType    |         |
|Identifier   |NA       |
|Refines      |         |
|Replaces     |NA       |
|Version      |NA       |
|DateIssued   |NA       |
|DateModified |NA       |
|Definition   |         |
|Comment      |         |

----

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">Ecological Traitdata Standard </span> by <span xmlns:cc="http://creativecommons.org/ns#" property="cc:attributionName">Florian D. Schneider, Nadja Simons, Caterina Penone, Andreas Ostrowski</span> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.

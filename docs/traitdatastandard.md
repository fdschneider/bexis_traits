# Ecological Traitdata Standard
Florian D. Schneider, Nadja Simons, Caterina Penone, Andreas Ostrowski  
12 Mai 2017  


**This is the documentation of the Ecological Traitdata Standard (ETS), version 0.3** 

This defined vocabulary aims at providing all essential columns for raw data of functional trait measurements for ecological research. Most terms relate to terms from the Darwin Core Standard and it's Extensions (terms of DWC are referenced thus in field 'Refines'; the full Darwin Core Standard can be found here: http://rs.tdwg.org/dwc/terms/index.htm)

The glossary of terms is ordered into a **core section** with essential columns for trait data, extensions which are allowing to provide additional layers of information, as well as a vocabulary for metadata information of particular importance for trait data. A final section provides defined terms for lists of trait definitions, also termed a Trait Thesaurus. 

**Extensions:**

- the `Occurence` extension contains information on the level of individual specimens, such as date and location and method of sampling and preservation, or physiological specifications of the phenotype, such as sex, life stage or age. 
- the `MeasurementOrFact` extension takes information at the level of single measurements or reported values, such as the original literature from where the value is cited, the method of measurement or statistical method of aggregation. 
- The extension `BiodiversityExploratories` provides columns for localisation for trait data from the Biodiversity Exploratories sites (ww.biodiversity-exploratories.de). 

**Structure of trait data:**

The traitdata standard requires data to be stored in a long table format containing one measurement per row described by the column terms provided in the core section. (see Whitepaper for further considerations)

There are two ways of integrating the extensions: 

- **within the same data file**: additional columns are provided to describe the properties concerning the measurement or the occurence of the specimen. The output file may be stored as a csv or txt table or an excel spreadsheet.  
- **in separate data files**: the main file refers to additional data files in the fields `measurementID` or `occurenceID`. This is usually the case if the occurences are externally documented, for instance as specimens from a museum. This also applies if the data are stored as an Excel spreadsheet or as a Darwin Core Archive (as proposed for TraitBank).   

This list of terms will also be available as 

- a csv/txt/xlsx table file which will be provided for download on BExIS including full documentation in the metadata (for manual use, this may be uploaded to BExIs as soon it's ready), and
- a machine readable template glossary (xml file or csv with additional flags and markers) which serves as input reference for software tools. (can we provide a simple API?) 



# Core traitdata columns

For the essential primary data (trait value, taxon assignment, trait name), the trait data standard recommends to report the original naming and value scheme as used by the data provider. However, to ensure compatibility with other datasets, the original data provider's information should be doubled into standardized columns indexed by appending `Std` to the column name. 
This ensures compatibility on the provider's side and transparency for data users on the reported measurements and facts, and enables checking for inconsistencies and misspellings in the complete dataset provided by the author. If provided, the standardized fields allow merging heterogeneous data sources into a single table to perform further analyses. This practice of double bookkeeping of trait data has successfully established for the TRY database on plant traits, for instance (Kattge ..). 

The R package 'traitdataform' (https://fdschneider.github.com/traitdataform) provides tools to transfer heterogeneous datasets into a longtable format and to create standardized taxa and trait columns, based on public ontologies. 

By linking to (public) ontologies via the field `taxonID`, further taxonomic information can be extracted for analysis. Alternatively, `taxonID` may also link to an accompanying datasheet that contains information on the taxonomic resolution or specification of the observation. 

Similarly, linking to trait terminologies (a 'Thesaurus') via the field `traitID` allows an unambiguous interpretation of the trait measurement. If no online ontology is available, an accompanying dataset should specify the trait definition. For setting up such a Thesaurus, we propose the use of terms provided in section 'Traitlist' below. 

## `scientificName`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#scientificname)

|             |scientificName                                                                                                        |
|:------------|:---------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                             |
|vocabulary   |                                                                                                                      |
|Identifier   |http://fdschneider.de/bexis_traits/traitdatastandard.html#scientificname                                              |
|Refines      |http://rs.tdwg.org/dwc/terms/scientificName                                                                           |
|Replaces     |NA                                                                                                                    |
|Version      |v0.3                                                                                                                  |
|DateIssued   |07.07.2017                                                                                                            |
|DateModified |NA                                                                                                                    |
|Definition   |Original character string provided as species name by the data owner (kept for reference only)                        |
|Comment      |Can be equal to scientificName. Authors may use abbreviations, or use underscores to separate genus and species name. |
## `taxonID`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#taxonid)

|             |taxonID                                                                                                                                                                                                                            |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |factor                                                                                                                                                                                                                             |
|vocabulary   |                                                                                                                                                                                                                                   |
|Identifier   |http://fdschneider.de/bexis_traits/traitdatastandard.html#taxonid                                                                                                                                                                  |
|Refines      |http://rs.tdwg.org/dwc/terms/taxonID                                                                                                                                                                                               |
|Replaces     |NA                                                                                                                                                                                                                                 |
|Version      |v0.3                                                                                                                                                                                                                               |
|DateIssued   |07.07.2017                                                                                                                                                                                                                         |
|DateModified |NA                                                                                                                                                                                                                                 |
|Definition   |Verified name identifier  of the species or subspecies (or higher taxon) for which this value was collected. Each entry should linkt to a published reference species  list/taxonomy. Avoid synonyms.                              |
|Comment      |Examples: "GBIF Backbone Taxonomy:497924", "8fa58e08-08de-4ac1-b69c-1235340b7001", "32567", "http://species.gbif.org/abies_alba_1753", "urn:lsid:gbif.org:usages:32567". For discussion see http://terms.tdwg.org/wiki/dwc:taxonID |
## `taxonRank`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#taxonrank)

|             |taxonRank                                                                                                                                                                                                                                                                                                                                                            |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |factor                                                                                                                                                                                                                                                                                                                                                               |
|vocabulary   |domain; kingdom; subkingdom; superhpylum; phylum; subphylum; superclass; class; subclass; supercohort; cohort; subcohort; superorder; order; subordern; infraorder; superfamily; family; subfamily; tribe; subtribe; genus; subgenus; section; subsection; series; subseries; speciesAggregate; species; subspecificAggregate; subspecies; variety; cultivar; strain |
|Identifier   |http://fdschneider.de/bexis_traits/traitdatastandard.html#taxonrank                                                                                                                                                                                                                                                                                                  |
|Refines      |http://rs.tdwg.org/dwc/terms/taxonRank                                                                                                                                                                                                                                                                                                                               |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                                   |
|Version      |v0.3                                                                                                                                                                                                                                                                                                                                                                 |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                                                                                           |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                                   |
|Definition   |The taxonomic rank of the most specific name in the scientificName. Recommended best practice is to use a controlled vocabulary.                                                                                                                                                                                                                                     |
|Comment      |This is to clarify cases where information is not given on a species level. Examples: "subspecies", "varietas", "forma", "species", "genus".                                                                                                                                                                                                                         |
## `kingdom`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#kingdom)

|             |kingdom                                                                                    |
|:------------|:------------------------------------------------------------------------------------------|
|valueType    |factor                                                                                     |
|vocabulary   |                                                                                           |
|Identifier   |http://fdschneider.de/bexis_traits/traitdatastandard.html#kingdom                          |
|Refines      |http://rs.tdwg.org/dwc/terms/kingdom                                                       |
|Replaces     |NA                                                                                         |
|Version      |v0.3                                                                                       |
|DateIssued   |07.07.2017                                                                                 |
|DateModified |NA                                                                                         |
|Definition   |The full scientific name of the kingdom in which the taxon is classified.                  |
|Comment      |Examples: "Animalia", "Plantae". For discussion see http://terms.tdwg.org/wiki/dwc:kingdom |
## `traitName`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#traitname)

|             |traitName                                                                                                                                                     |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                     |
|vocabulary   |                                                                                                                                                              |
|Identifier   |http://fdschneider.de/bexis_traits/traitdatastandard.html#traitname                                                                                           |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementType                                                                                                                  |
|Replaces     |NA                                                                                                                                                            |
|Version      |v0.3                                                                                                                                                          |
|DateIssued   |07.07.2017                                                                                                                                                    |
|DateModified |NA                                                                                                                                                            |
|Definition   |Name of the trait as used by the data provider (kept for compatibility on provider side).                                                                     |
|Comment      |This can be a short name or user defined coded trait name. However, it is recommended to provide definition of the user provided trait names in the metadata. |
## `traitID`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#traitid)

|             |traitID                                                                             |
|:------------|:-----------------------------------------------------------------------------------|
|valueType    |factor                                                                              |
|vocabulary   |see traitlist                                                                       |
|Identifier   |http://fdschneider.de/bexis_traits/traitdatastandard.html#traitid                   |
|Refines      |                                                                                    |
|Replaces     |NA                                                                                  |
|Version      |v0.3                                                                                |
|DateIssued   |07.07.2017                                                                          |
|DateModified |NA                                                                                  |
|Definition   |Unique identifier of the trait following the thesaurus of traits available on BExIS |
|Comment      |                                                                                    |
## `traitValue`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#traitvalue)

|             |traitValue                                                                                                                                                                                   |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                    |
|vocabulary   |                                                                                                                                                                                             |
|Identifier   |http://fdschneider.de/bexis_traits/traitdatastandard.html#traitvalue                                                                                                                         |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementValue                                                                                                                                                |
|Replaces     |NA                                                                                                                                                                                           |
|Version      |v0.3                                                                                                                                                                                         |
|DateIssued   |07.07.2017                                                                                                                                                                                   |
|DateModified |NA                                                                                                                                                                                           |
|Definition   |Measured raw value or factor level for this species trait as measured and provided by the author.                                                                                            |
|Comment      |Must respect the unit given in 'measurementUnit_user' for numerical traits. For categorical traits, the factor levels should be harmonized across the dataset and explained in the metadata. |
## `traitUnit`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#traitunit)

|             |traitUnit                                                                                                                                                                     |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                     |
|vocabulary   |                                                                                                                                                                              |
|Identifier   |http://fdschneider.de/bexis_traits/traitdatastandard.html#traitunit                                                                                                           |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementUnit                                                                                                                                  |
|Replaces     |NA                                                                                                                                                                            |
|Version      |v0.3                                                                                                                                                                          |
|DateIssued   |07.07.2017                                                                                                                                                                    |
|DateModified |NA                                                                                                                                                                            |
|Definition   |Reports the unit that the author's raw data were measured in, if applicable (only for numeric values).                                                                        |
|Comment      |For numerical values report unit in format for lengths "mm", for volumes "mm3" / "mm^3", areas "mm2" / "mm^2", for movement "m/s", or for volume to surface ratios: "mm3/mm2" |
## `scientificNameStd`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#scientificnamestd)

|             |scientificNameStd                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|Identifier   |http://fdschneider.de/bexis_traits/traitdatastandard.html#scientificnamestd                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|Refines      |http://rs.tdwg.org/dwc/terms/scientificName                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|Version      |v0.3                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|Definition   |Full scientific name (with authorship and date information if known). It should be an accepted taxon name according to a published taxonomy (provided in taxonID).                                                                                                                                                                                                                                                                                                                                                                                                                  |
|Comment      |Provide reference taxonomy in metadata of the dataset. Examples: "Coleoptera" (order), "Vespertilionidae" (family), "Manis" (genus), "Ctenomys sociabilis" (genus + specificEpithet), "Ambystoma tigrinum diaboli" (genus + specificEpithet + infraspecificEpithet), "Roptrocerus typographi (Györfi, 1952)" (genus + specificEpithet + scientificNameAuthorship), "Quercus agrifolia var. oxyadenia (Torr.) J.T. Howell" (genus + specificEpithet + taxonRank + infraspecificEpithet + scientificNameAuthorship). For discussion see http://terms.tdwg.org/wiki/dwc:scientificName |
## `traitNameStd`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#traitnamestd)

|             |traitNameStd                                                                                                                                                        |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |factor                                                                                                                                                              |
|vocabulary   |                                                                                                                                                                    |
|Identifier   |http://fdschneider.de/bexis_traits/traitdatastandard.html#traitnamestd                                                                                              |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementType                                                                                                                        |
|Replaces     |NA                                                                                                                                                                  |
|Version      |v0.3                                                                                                                                                                |
|DateIssued   |07.07.2017                                                                                                                                                          |
|DateModified |NA                                                                                                                                                                  |
|Definition   |Descriptive Name of the trait reported. This should follow the controlled vocabulary of a thesaurus of traits available online or published along with the dataset. |
|Comment      |Accompanying this, the traitID should provide an unambiguous link to the trait definition in the thesaurus or supplementary dataset.                                |
## `traitValueStd`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#traitvaluestd)

|             |traitValueStd                                                                                                                                                                                         |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                             |
|vocabulary   |                                                                                                                                                                                                      |
|Identifier   |http://fdschneider.de/bexis_traits/traitdatastandard.html#traitvaluestd                                                                                                                               |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementValue                                                                                                                                                         |
|Replaces     |NA                                                                                                                                                                                                    |
|Version      |v0.3                                                                                                                                                                                                  |
|DateIssued   |07.07.2017                                                                                                                                                                                            |
|DateModified |NA                                                                                                                                                                                                    |
|Definition   |Standardised measured value or factor level for this species trait. Numerical values must use the correct unit. Factor levels  must be compliant with the thesaurus of traits.                        |
|Comment      |Using "." as a decimal separator! The standardized data values or factor levels must correspond to the expected units and factor levels of the trait thesaurus, e.g. "32.423", "female", "apter", "3" |
## `traitUnitStd`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#traitunitstd)

|             |traitUnitStd                                                                                                                                                                    |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                       |
|vocabulary   |                                                                                                                                                                                |
|Identifier   |http://fdschneider.de/bexis_traits/traitdatastandard.html#traitunitstd                                                                                                          |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementUnit                                                                                                                                    |
|Replaces     |NA                                                                                                                                                                              |
|Version      |v0.3                                                                                                                                                                            |
|DateIssued   |07.07.2017                                                                                                                                                                      |
|DateModified |NA                                                                                                                                                                              |
|Definition   |The units associated with the measurementValue. The expected standard unit for this trait as defined in the traitlist/ thesaurus.                                               |
|Comment      |Recommended best practice is to use the International System of Units (SI).  Examples: "mm", "C", "km", "ha". For discussion see http://terms.tdwg.org/wiki/dwc:measurementUnit |
## `measurementID`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#measurementid)

|             |measurementID                                                                                                                                                                                                                                                                                                                                                              |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                                                                                                                                                                                                  |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                                           |
|Identifier   |http://fdschneider.de/bexis_traits/traitdatastandard.html#measurementid                                                                                                                                                                                                                                                                                                    |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementID                                                                                                                                                                                                                                                                                                                                 |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                                         |
|Version      |v0.3                                                                                                                                                                                                                                                                                                                                                                       |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                                                                                                 |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                                         |
|Definition   |A unique, dataset-specific identifier. Links multi-value trait measurements, e.g. x-y-z coordinates of a morphometric landmark, biochemical compound quantities for different chainlengths. In this case, the trait names must specifiy the sub-measurement, e.g. "landmark32_x", and must be specified in a reference trait list, given in the field "measurementMethod". |
|Comment      |                                                                                                                                                                                                                                                                                                                                                                           |
## `occurenceID`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#occurenceid)

|             |occurenceID                                                                                                                                                                                                                                                                                                                                                                                                |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                                                                                                                                                                                                                                  |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                                                                           |
|Identifier   |http://fdschneider.de/bexis_traits/traitdatastandard.html#occurenceid                                                                                                                                                                                                                                                                                                                                      |
|Refines      |http://rs.tdwg.org/dwc/terms/occurrenceID                                                                                                                                                                                                                                                                                                                                                                  |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                                                                         |
|Version      |v0.3                                                                                                                                                                                                                                                                                                                                                                                                       |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                                                                                                                                 |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                                                                         |
|Definition   |A character string user defined by the data author.  It is recommended best practice to use a globally unique identifier, if available, e.g. a museum ID referring to the individual specimen from which the data were measured. usually does not apply for literature data.                                                                                                                               |
|Comment      |This is important for the analysis of co-variation of morphometric data or intraspecific variation. It may also couples multiple measurements on a single specimen, which also could be a leaf or a single bone without an assignment to an individual organism. If available, upload related dataset to describe specimens more precisely, e.g. environmental parameters or identity related information. |
## `warnings`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#warnings)

|             |warnings                                                                                                                                                                                                                                                                                                              |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                                                                                                                                             |
|vocabulary   |                                                                                                                                                                                                                                                                                                                      |
|Identifier   |                                                                                                                                                                                                                                                                                                                      |
|Refines      |                                                                                                                                                                                                                                                                                                                      |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                    |
|Version      |v0.3                                                                                                                                                                                                                                                                                                                  |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                                            |
|DateModified |NA                                                                                                                                                                                                                                                                                                                    |
|Definition   |warnings from the R-script will be stored here, e.g. ragarding a lack of match between the provided taxonID and the ontology, or the trait names or values, a mismatch in the units provided and the unit expected according to the trait table. User defined warnings and flags can be added as well, e.g. 'NOTUSE'. |
|Comment      |                                                                                                                                                                                                                                                                                                                      |

# Extension: Measurement or Fact 

This section provides additional information about a reported measurement or fact and in most cases can easily be included as extra columns to the core dataset. The columns would contain detail on the methodology of measuring and reporting of aggregated data. 

In case of facts reported from literature or from expert knowledge, or cited from other databases, please include bibliographic citation of the original data source in field 'references'. 

## `basisOfRecord`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#basisofrecord)

|             |basisOfRecord                                                                                                                                                                                                                            |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |factor                                                                                                                                                                                                                                   |
|vocabulary   |LivingSpecimen; PreservedSpecimen; FossilSpecimen; literatureData; traitDatabase; expertKnowledge                                                                                                                                        |
|Identifier   |                                                                                                                                                                                                                                         |
|Refines      |http://rs.tdwg.org/dwc/terms/basisOfRecord                                                                                                                                                                                               |
|Replaces     |NA                                                                                                                                                                                                                                       |
|Version      |v0.3                                                                                                                                                                                                                                     |
|DateIssued   |07.07.2017                                                                                                                                                                                                                               |
|DateModified |NA                                                                                                                                                                                                                                       |
|Definition   |How and from which kind of specimen were the data obtained? Use of the controlled vocabulary is recommended.                                                                                                                             |
|Comment      |Options are: Taken by own measurement (distinguish LivingSpecimen, PreservedSpecimen, FossilSpecimen) or taken from literature (literatureData), from an existing trait database (traitDatabase), or expert knowledge (expertKnowledge). |
## `basisOfRecordDescription`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#basisofrecorddescription)

|             |basisOfRecordDescription                                                                                                                                                                                                                                                                                                          |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                                                                                                                                                         |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                  |
|Identifier   |                                                                                                                                                                                                                                                                                                                                  |
|Refines      |                                                                                                                                                                                                                                                                                                                                  |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                |
|Version      |v0.3                                                                                                                                                                                                                                                                                                                              |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                                                        |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                |
|Definition   |Adding more detail to the basisOfRecord.                                                                                                                                                                                                                                                                                          |
|Comment      |If life specimens were sampled, where did they come from? Have they been reared in cultivation? If literature data or online database, provide type of literature, e.g. textbook, website, URL, etc. If preserved specimens were used, which method of preservation? In case of expert knowledge, give the name of the authority. |
## `references`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#references)

|             |references                                                                                                                                                                                                                                                                                                            |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                                                                                                                                             |
|vocabulary   |                                                                                                                                                                                                                                                                                                                      |
|Identifier   |                                                                                                                                                                                                                                                                                                                      |
|Refines      |http://purl.org/dc/terms/references                                                                                                                                                                                                                                                                                   |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                    |
|Version      |v0.3                                                                                                                                                                                                                                                                                                                  |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                                            |
|DateModified |NA                                                                                                                                                                                                                                                                                                                    |
|Definition   |Precise reference to the source. If literature data, this should quote the book or online database. If museum this should report the name of the collection. If expert knowledge, this should name the authority. If trait database, provide reference to the original publication, DOI or URL of the trait-database. |
|Comment      |Examples: "http://mvzarctos.berkeley.edu/guid/MVZ:Mamm:165861"; "http://www.catalogueoflife.org/annual-checklist/show_species_details.php?record_id=6197868". For discussion see http://terms.tdwg.org/wiki/dwc:references                                                                                            |
## `measurementResolution`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#measurementresolution)

|             |measurementResolution                                                                                                                                                                                                                       |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                                                                   |
|vocabulary   |                                                                                                                                                                                                                                            |
|Identifier   |                                                                                                                                                                                                                                            |
|Refines      |                                                                                                                                                                                                                                            |
|Replaces     |NA                                                                                                                                                                                                                                          |
|Version      |v0.3                                                                                                                                                                                                                                        |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                  |
|DateModified |NA                                                                                                                                                                                                                                          |
|Definition   |If the trait information was originally given on another taxonomic level than species. Applies mainly for literature and expert knowledge data. not applying for measured data. The hierarchical level to which the trait data would refer. |
|Comment      |For example, information given in literature could state 'most species in this genus are winged', but the trait data could be given for each species in this genus.                                                                         |
## `measurementMethod`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#measurementmethod)

|             |measurementMethod                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|Identifier   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementMethod                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|Version      |v0.3                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|Definition   |Applies primarily to measured data. The method, tools and scales used to measure a (numerical) trait value. A description of or reference to (publication, URI) the method or protocol used to determine the measurement, fact, characteristic, or assertion.                                                                                                                                                                                                                                                            |
|Comment      |Should be a concise and standardised text entry or reference (publication, URI), referring to a particular method (e.g. 'direct weighing', 'length-mass regression', 'intertegular span', 'length between node X and y' ) and  measurement conditions (e.g. certain temperature or humidity, name of device or scale used for measurement).  A more detailed description of the method or protocol used to determine the measurement, fact, characteristic, or assertion should be given in the metadata of the dataset. |
## `measurementDeterminedBy`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#measurementdeterminedby)

|             |measurementDeterminedBy                                                                                                                                                                                                                                     |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                                                                                   |
|vocabulary   |                                                                                                                                                                                                                                                            |
|Identifier   |                                                                                                                                                                                                                                                            |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementDeterminedBy                                                                                                                                                                                                        |
|Replaces     |NA                                                                                                                                                                                                                                                          |
|Version      |v0.3                                                                                                                                                                                                                                                        |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                  |
|DateModified |NA                                                                                                                                                                                                                                                          |
|Definition   |A list (concatenated and separated) of names of people, groups, or organizations who determined the value of the measurement. Can be encoded by dataset-specific identifiers for reasons of privacy. This is kept as a co-factor for repeated measurements. |
|Comment      |The recommended best practice is to separate the values with a vertical bar (' &#124; '). Examples: "Rob Guralnick", "Julie Woodruff &#124; Eileen Lacey".                                                                                                  |
## `measurementDeterminedDate`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#measurementdetermineddate)

|             |measurementDeterminedDate                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |Date                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|Identifier   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementDeterminedDate                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|Version      |v0.3                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|Definition   |The date of the measurement. Also kept as a co-factor. Use format "YYYY-MM-DD hh:mm TIMEZONE". Not to confuse with year, month, day columns which are reserved for the date of sampling (may be identical, though).                                                                                                                                                                                                                                                                                  |
|Comment      |Examples: "1963-03-08T14:07-0600" is 8 Mar 1963 2:07pm in the time zone six hours earlier than UTC, "2009-02-20T08:40Z" is 20 Feb 2009 8:40am UTC, "1809-02-12" is 12 Feb 1809, "1906-06" is Jun 1906, "1971" is just that year, "2007-03-01T13:00:00Z/2008-05-11T15:30:00Z" is the interval between 1 Mar 2007 1pm UTC and 11 May 2008 3:30pm UTC, "2007-11-13/15" is the interval between 13 Nov 2007 and 15 Nov 2007. For discussion see http://terms.tdwg.org/wiki/dwc:measurementDeterminedDate |
## `measurementRemarks`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#measurementremarks)

|             |measurementRemarks                                                                                                                        |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                 |
|vocabulary   |                                                                                                                                          |
|Identifier   |                                                                                                                                          |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementRemarks                                                                                           |
|Replaces     |NA                                                                                                                                        |
|Version      |v0.3                                                                                                                                      |
|DateIssued   |07.07.2017                                                                                                                                |
|DateModified |NA                                                                                                                                        |
|Definition   |Remarks concerning a particular measurement, e.g. additional information on the quality and reliability, reference or acknowledgements.   |
|Comment      |Any particularities about the individual measurement or specimen that might affect trait measuremnt, e.g. 'last antenna segment missing'. |
## `aggregateMeasure`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#aggregatemeasure)

|             |aggregateMeasure                                                                                                                                                                                                                                                                                               |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |logical                                                                                                                                                                                                                                                                                                        |
|vocabulary   |                                                                                                                                                                                                                                                                                                               |
|Identifier   |                                                                                                                                                                                                                                                                                                               |
|Refines      |                                                                                                                                                                                                                                                                                                               |
|Replaces     |NA                                                                                                                                                                                                                                                                                                             |
|Version      |v0.3                                                                                                                                                                                                                                                                                                           |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                                     |
|DateModified |NA                                                                                                                                                                                                                                                                                                             |
|Definition   |Is measurementValue reporting an individual measurement or an aggregate Measure? Takes a binary entry: TRUE or FALSE                                                                                                                                                                                           |
|Comment      |This is flagging aggregate data in an unambiguous way. Aggregate measures are often reported for repeated measures, e.g. replicate measurements of leaf size from a single plant individual or for grouped measurement, e.g. for weightings of a counted number of specimens (e.g. leaves or small organisms). |
## `individualCount`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#individualcount)

|             |individualCount                                                                                                                                      |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |integer                                                                                                                                              |
|vocabulary   |                                                                                                                                                     |
|Identifier   |                                                                                                                                                     |
|Refines      |http://rs.tdwg.org/dwc/terms/individualCount                                                                                                         |
|Replaces     |NA                                                                                                                                                   |
|Version      |v0.3                                                                                                                                                 |
|DateIssued   |07.07.2017                                                                                                                                           |
|DateModified |NA                                                                                                                                                   |
|Definition   |If measurement is an aggregate measure of multiple individuals or specimens, report number of specimens as count, i.e. integer number. Defaults to 1 |
|Comment      |Examples: "1", "25". For discussion see http://terms.tdwg.org/wiki/dwc:individualCount                                                               |
## `dispersion`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#dispersion)

|             |dispersion                                                                                                                                                                                                                                                                                                                                |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |numeric                                                                                                                                                                                                                                                                                                                                   |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                          |
|Identifier   |                                                                                                                                                                                                                                                                                                                                          |
|Refines      |                                                                                                                                                                                                                                                                                                                                          |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                        |
|Version      |v0.3                                                                                                                                                                                                                                                                                                                                      |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                                                                |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                        |
|Definition   |If aggregate measure of multiple individuals or specimens, the numeric value of dispersion (variance or standard deviation) for the mean value reported in measurementValue_user (no unit conversion is provided by the R-package!). Defaults to 0. If a value is provided, report the statistical method in the field statisticalMethod. |
|Comment      |                                                                                                                                                                                                                                                                                                                                          |
## `measurementValue_min`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#measurementvalue_min)

|             |measurementValue_min                                                                   |
|:------------|:--------------------------------------------------------------------------------------|
|valueType    |numeric                                                                                |
|vocabulary   |                                                                                       |
|Identifier   |                                                                                       |
|Refines      |                                                                                       |
|Replaces     |NA                                                                                     |
|Version      |v0.3                                                                                   |
|DateIssued   |07.07.2017                                                                             |
|DateModified |NA                                                                                     |
|Definition   |The lower boundary of observed values. Instead of or in addition to dispersion metric. |
|Comment      |                                                                                       |
## `measurementValue_max`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#measurementvalue_max)

|             |measurementValue_max                                                                   |
|:------------|:--------------------------------------------------------------------------------------|
|valueType    |numeric                                                                                |
|vocabulary   |                                                                                       |
|Identifier   |                                                                                       |
|Refines      |                                                                                       |
|Replaces     |NA                                                                                     |
|Version      |v0.3                                                                                   |
|DateIssued   |07.07.2017                                                                             |
|DateModified |NA                                                                                     |
|Definition   |The upper boundary of observed values. Instead of or in addition to dispersion metric. |
|Comment      |                                                                                       |
## `measurementAccuracy`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#measurementaccuracy)

|             |measurementAccuracy                                                                                                                  |
|:------------|:------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                            |
|vocabulary   |                                                                                                                                     |
|Identifier   |                                                                                                                                     |
|Refines      |http://rs.tdwg.org/dwc/terms/measurementAccuracy                                                                                     |
|Replaces     |NA                                                                                                                                   |
|Version      |v0.3                                                                                                                                 |
|DateIssued   |07.07.2017                                                                                                                           |
|DateModified |NA                                                                                                                                   |
|Definition   |The description of the potential error associated with the measurementValue.                                                         |
|Comment      |Examples: "0.01", "normal distribution with variation of 2 m". For discussion see http://terms.tdwg.org/wiki/dwc:measurementAccuracy |
## `statisticalMethod`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#statisticalmethod)

|             |statisticalMethod                                                                                                                                               |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                       |
|vocabulary   |                                                                                                                                                                |
|Identifier   |                                                                                                                                                                |
|Refines      |                                                                                                                                                                |
|Replaces     |NA                                                                                                                                                              |
|Version      |v0.3                                                                                                                                                            |
|DateIssued   |07.07.2017                                                                                                                                                      |
|DateModified |NA                                                                                                                                                              |
|Definition   |For aggregated measures, the method for data aggregation or averaging as well as the variation or range.                                                        |
|Comment      |E.g. 'mean and standard deviation', 'median and 95% confidence interval', 'mean and variance', 'mean and range of values', 'median and 95% interquantile range' |


# Extension: Occurence 

this section of columns aims for identifying the methodology and primary source of the data and keep the reference to the actual specimen (e.g. for museum collections or related data analysis). It also may add detail on the condition of the observed specimen, its sex, morphotype or developmental stage. 
Especially for analyses of intra-specific trait variation, this composes valuable data. 

For trait data compiled from literature or expert knowledge, the level of information on an 'occurence' would not apply, since no specific individual has been observed. In this case, the field 'occurenceID' should be left blank in the core data.  

## `sex`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#sex)

|             |sex                                                                                                                                                         |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |factor                                                                                                                                                      |
|vocabulary   |male; female; subadult; unknown; hermaphrodite                                                                                                              |
|Identifier   |                                                                                                                                                            |
|Refines      |http://rs.tdwg.org/dwc/terms/sex                                                                                                                            |
|Replaces     |NA                                                                                                                                                          |
|Version      |v0.3                                                                                                                                                        |
|DateIssued   |07.07.2017                                                                                                                                                  |
|DateModified |NA                                                                                                                                                          |
|Definition   |Defining the sex of the measured specimen, to capture dimorphisms. Standardised factor levels are: "male", "female", "subadult", "unknown", "hermaphrodite" |
|Comment      |                                                                                                                                                            |
## `lifeStage`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#lifestage)

|             |lifeStage                                                                                                                                                                                                                                                  |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                                                                                  |
|vocabulary   |                                                                                                                                                                                                                                                           |
|Identifier   |                                                                                                                                                                                                                                                           |
|Refines      |http://rs.tdwg.org/dwc/terms/lifeStage                                                                                                                                                                                                                     |
|Replaces     |NA                                                                                                                                                                                                                                                         |
|Version      |v0.3                                                                                                                                                                                                                                                       |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                 |
|DateModified |NA                                                                                                                                                                                                                                                         |
|Definition   |The life stage of the measured specimen.                                                                                                                                                                                                                   |
|Comment      |Recommended factor levels are: seed, seedling, sapling, adult, egg, larval_instar_1, larval_instar_2, larval_instar_3, ... , pupa; For very taxon-specific life stages, it is recommended to provide detailled explanation in the metadata of the dataset. |
## `age`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#age)

|             |age                               |
|:------------|:---------------------------------|
|valueType    |numeric                           |
|vocabulary   |                                  |
|Identifier   |                                  |
|Refines      |                                  |
|Replaces     |NA                                |
|Version      |v0.3                              |
|DateIssued   |07.07.2017                        |
|DateModified |NA                                |
|Definition   |The age of the specimen in years. |
|Comment      |Example: "2", "0.16".             |
## `morphotype`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#morphotype)

|             |morphotype                                                                                                                                                    |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                     |
|vocabulary   |                                                                                                                                                              |
|Identifier   |                                                                                                                                                              |
|Refines      |                                                                                                                                                              |
|Replaces     |NA                                                                                                                                                            |
|Version      |v0.3                                                                                                                                                          |
|DateIssued   |07.07.2017                                                                                                                                                    |
|DateModified |NA                                                                                                                                                            |
|Definition   |The morphotype of the observed specimen.                                                                                                                      |
|Comment      |Examples: "worker", "drone", "queen". Since morphotypes can differ between organism groups, provide definition of morphotypes in the metadata of the dataset. |
## `eventID`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#eventid)

|             |eventID                                                                                                                                                                                                                                                         |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                                                                                       |
|vocabulary   |                                                                                                                                                                                                                                                                |
|Identifier   |                                                                                                                                                                                                                                                                |
|Refines      |http://rs.tdwg.org/dwc/terms/eventID                                                                                                                                                                                                                            |
|Replaces     |NA                                                                                                                                                                                                                                                              |
|Version      |v0.3                                                                                                                                                                                                                                                            |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                      |
|DateModified |NA                                                                                                                                                                                                                                                              |
|Definition   |The sampling event or campaign. User specified character string. could link to another table that provides more information, e.g. environmental or temporal parameters, descriptions on methods etc.. should link to official Exploratories sampling campaigns. |
|Comment      |                                                                                                                                                                                                                                                                |
## `preparations`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#preparations)

|             |preparations                                                                                                                                                                                                                                                                                        |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                                                                                                                           |
|vocabulary   |                                                                                                                                                                                                                                                                                                    |
|Identifier   |                                                                                                                                                                                                                                                                                                    |
|Refines      |http://rs.tdwg.org/dwc/terms/preparations                                                                                                                                                                                                                                                           |
|Replaces     |NA                                                                                                                                                                                                                                                                                                  |
|Version      |v0.3                                                                                                                                                                                                                                                                                                |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                          |
|DateModified |NA                                                                                                                                                                                                                                                                                                  |
|Definition   |For preserved specimens, a list (concatenated and separated) of preparations and preservation methods for a specimen.                                                                                                                                                                               |
|Comment      |The recommended best practice is to separate the values with a vertical bar (' &#124; '). Examples: "fossil", "cast", "photograph", "DNA extract", "skin &#124; "skull &#124; skeleton", "whole animal (ETOH) &#124; tissue (EDTA)". For discussion see http://terms.tdwg.org/wiki/dwc:preparations |
## `samplingProtocol`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#samplingprotocol)

|             |samplingProtocol                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|Identifier   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|Refines      |http://rs.tdwg.org/dwc/terms/samplingProtocol                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|Version      |v0.3                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|Definition   |The name of, reference to, or description of the method or protocol used for obtaining the specimen.                                                                                                                                                                                                                                                                                                                                                                                                                |
|Comment      |Examples: "UV light trap", "mist net", "bottom trawl", "ad hoc observation", "point count", "Penguins from space: faecal stains reveal the location of emperor penguin colonies, http://dx.doi.org/10.1111/j.1466-8238.2009.00467.x", "Takats et al. 2001. Guidelines for Nocturnal Owl Monitoring in North America. Beaverhill Bird Observatory and Bird Studies Canada, Edmonton, Alberta. 32 pp.", "http://www.bsc-eoc.org/download/Owl.pdf". For discussion see http://terms.tdwg.org/wiki/dwc:samplingProtocol |
## `year`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#year)

|             |year                                                                    |
|:------------|:-----------------------------------------------------------------------|
|valueType    |integer                                                                 |
|vocabulary   |                                                                        |
|Identifier   |                                                                        |
|Refines      |http://rs.tdwg.org/dwc/terms/year                                       |
|Replaces     |NA                                                                      |
|Version      |v0.3                                                                    |
|DateIssued   |07.07.2017                                                              |
|DateModified |NA                                                                      |
|Definition   |The four-digit year, at which the specimens were extracted or sampled.  |
|Comment      |Example: "2008". For discussion see http://terms.tdwg.org/wiki/dwc:year |
## `month`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#month)

|             |month                                                                                              |
|:------------|:--------------------------------------------------------------------------------------------------|
|valueType    |integer                                                                                            |
|vocabulary   |                                                                                                   |
|Identifier   |                                                                                                   |
|Refines      |http://rs.tdwg.org/dwc/terms/month                                                                 |
|Replaces     |NA                                                                                                 |
|Version      |v0.3                                                                                               |
|DateIssued   |07.07.2017                                                                                         |
|DateModified |NA                                                                                                 |
|Definition   |The ordinal month, in which the specimens were extracted or sampled.                               |
|Comment      |Examples: "1" (=January), "10" (=October). For discussion see http://terms.tdwg.org/wiki/dwc:month |
## `day`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#day)

|             |day                                                                            |
|:------------|:------------------------------------------------------------------------------|
|valueType    |integer                                                                        |
|vocabulary   |                                                                               |
|Identifier   |                                                                               |
|Refines      |http://rs.tdwg.org/dwc/terms/day                                               |
|Replaces     |NA                                                                             |
|Version      |v0.3                                                                           |
|DateIssued   |07.07.2017                                                                     |
|DateModified |NA                                                                             |
|Definition   |The integer day of the month on which the specimens were extracted or sampled. |
|Comment      |Examples: "9", "28". For discussion see http://terms.tdwg.org/wiki/dwc:day     |
## `eventDate`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#eventdate)

|             |eventDate                                                                                                                                                                                                                                                                                                                                    |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |Date                                                                                                                                                                                                                                                                                                                                         |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                             |
|Identifier   |                                                                                                                                                                                                                                                                                                                                             |
|Refines      |http://rs.tdwg.org/dwc/terms/eventDate                                                                                                                                                                                                                                                                                                       |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                           |
|Version      |v0.3                                                                                                                                                                                                                                                                                                                                         |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                                                                   |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                           |
|Definition   |Represents the date, at which the specimens were extracted or sampled. If providing eventDate, then enter format of type: YYYY-MM-DD hh:mm TIMEZONE (fall back to 12:00 if no time is available).                                                                                                                                            |
|Comment      |For lower precision, use year, month and day field instead. Note: this is not to record the date when the specimens were measured (use measurementDeterminedDate for this). If applicable, at least provide a year. This is particularly important if the measurements were taken from specimens from the exploratories or museum specimens. |
## `locationID`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#locationid)

|             |locationID                                                                                                                                                                                                                             |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |factor                                                                                                                                                                                                                                 |
|vocabulary   |                                                                                                                                                                                                                                       |
|Identifier   |                                                                                                                                                                                                                                       |
|Refines      |http://rs.tdwg.org/dwc/terms/locationID                                                                                                                                                                                                |
|Replaces     |NA                                                                                                                                                                                                                                     |
|Version      |v0.3                                                                                                                                                                                                                                   |
|DateIssued   |07.07.2017                                                                                                                                                                                                                             |
|DateModified |NA                                                                                                                                                                                                                                     |
|Definition   |A unique, dataset-specific identifier. Could report the subplot within the Exploratories, or the plot or replicate of a separate experimental setting. If further information is available, specify locationIDs in a separate dataset. |
|Comment      |                                                                                                                                                                                                                                       |
## `habitat`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#habitat)

|             |habitat                                                                                                                                             |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |factor                                                                                                                                              |
|vocabulary   |                                                                                                                                                    |
|Identifier   |                                                                                                                                                    |
|Refines      |http://rs.tdwg.org/dwc/terms/habitat                                                                                                                |
|Replaces     |NA                                                                                                                                                  |
|Version      |v0.3                                                                                                                                                |
|DateIssued   |07.07.2017                                                                                                                                          |
|DateModified |NA                                                                                                                                                  |
|Definition   |A character string reporting habitat type from which the specimen was sampled. E.g. 'forest', 'grassland', 'oak savanna', 'pre-cordilleran steppe'. |
|Comment      |                                                                                                                                                    |
## `decimalLongitude`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#decimallongitude)

|             |decimalLongitude                                                                                                                                                                                                                  |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |numeric                                                                                                                                                                                                                           |
|vocabulary   |                                                                                                                                                                                                                                  |
|Identifier   |                                                                                                                                                                                                                                  |
|Refines      |http://rs.tdwg.org/dwc/terms/decimalLongitude                                                                                                                                                                                     |
|Replaces     |NA                                                                                                                                                                                                                                |
|Version      |v0.3                                                                                                                                                                                                                              |
|DateIssued   |07.07.2017                                                                                                                                                                                                                        |
|DateModified |NA                                                                                                                                                                                                                                |
|Definition   |The geographic longitude (in decimal degrees, using the spatial reference system given in geodeticDatum) of the geographic center of a Location.                                                                                  |
|Comment      |Positive values are east of the Greenwich Meridian, negative values are west of it. Legal values lie between -180 and 180, inclusive. Example: "-121.1761111". For discussion see http://terms.tdwg.org/wiki/dwc:decimalLongitude |
## `decimalLatitude`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#decimallatitude)

|             |decimalLatitude                                                                                                                                                                                                    |
|:------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |numeric                                                                                                                                                                                                            |
|vocabulary   |                                                                                                                                                                                                                   |
|Identifier   |                                                                                                                                                                                                                   |
|Refines      |http://rs.tdwg.org/dwc/terms/decimalLatitude                                                                                                                                                                       |
|Replaces     |NA                                                                                                                                                                                                                 |
|Version      |v0.3                                                                                                                                                                                                               |
|DateIssued   |07.07.2017                                                                                                                                                                                                         |
|DateModified |NA                                                                                                                                                                                                                 |
|Definition   |The geographic latitude (in decimal degrees, using the spatial reference system given in geodeticDatum) of the geographic center of a Location.                                                                    |
|Comment      |Positive values are north of Equator, negative values are south of it. Legal values lie between -180 and 180, inclusive. Example: "-41.0983423". For discussion see http://terms.tdwg.org/wiki/dwc:decimalLatitude |
## `elevation`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#elevation)

|             |elevation                                                                                                                                                                                                                                                                                                                                          |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |numeric                                                                                                                                                                                                                                                                                                                                            |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                   |
|Identifier   |                                                                                                                                                                                                                                                                                                                                                   |
|Refines      |http://rs.tdwg.org/dwc/terms/verbatimElevation                                                                                                                                                                                                                                                                                                     |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                 |
|Version      |v0.3                                                                                                                                                                                                                                                                                                                                               |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                                                                         |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                 |
|Definition   |The geographic elevation in meters above sea level.                                                                                                                                                                                                                                                                                                |
|Comment      |May map to verbatimElevation (http://rs.tdwg.org/dwc/terms/verbatimElevation) or minimumElevationInMeters (http://rs.tdwg.org/dwc/terms/minimumElevationInMeters) and maximumElevationInMeters (http://rs.tdwg.org/dwc/terms/maximumElevationInMeters); Example: "200". For discussion see http://terms.tdwg.org/wiki/dwc:maximumElevationInMeters |
## `geodeticDatum`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#geodeticdatum)

|             |geodeticDatum                                                                                                                                                                                                                                                                                                                                            |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |factor                                                                                                                                                                                                                                                                                                                                                   |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                         |
|Identifier   |                                                                                                                                                                                                                                                                                                                                                         |
|Refines      |http://rs.tdwg.org/dwc/terms/geodeticDatum                                                                                                                                                                                                                                                                                                               |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                       |
|Version      |v0.3                                                                                                                                                                                                                                                                                                                                                     |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                                                                               |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                       |
|Definition   |The geodeticDatum defines the ellipsoid, geodetic datum, or spatial reference system (SRS) upon which the geographic coordinates given in decimalLatitude and decimalLongitude as based. Recommended system is "WGS84". Use the EPSG code to provide an SRS. Examples: "EPSG:4326", "WGS84", "NAD27", "Campo Inchauspe", "European 1950", "Clarke 1866"* |
|Comment      |                                                                                                                                                                                                                                                                                                                                                         |
## `verbatimLocality`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#verbatimlocality)

|             |verbatimLocality                                                                                                                                                                                                                                                                                                                                           |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                                                                                                                                                                                  |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                           |
|Identifier   |                                                                                                                                                                                                                                                                                                                                                           |
|Refines      |http://rs.tdwg.org/dwc/terms/verbatimLocality                                                                                                                                                                                                                                                                                                              |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                                         |
|Version      |v0.3                                                                                                                                                                                                                                                                                                                                                       |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                                                                                 |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                                         |
|Definition   |The specific description of the place. Less specific geographic information can be provided in other geographic terms (higherGeography, continent, country, stateProvince, county, municipality, waterBody, island, islandGroup). This term may contain information modified from the original to correct perceived errors or standardize the description. |
|Comment      |                                                                                                                                                                                                                                                                                                                                                           |
## `country`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#country)

|             |country                                                                                                                                                                                                              |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                                            |
|vocabulary   |                                                                                                                                                                                                                     |
|Identifier   |                                                                                                                                                                                                                     |
|Refines      |http://rs.tdwg.org/dwc/terms/country                                                                                                                                                                                 |
|Replaces     |NA                                                                                                                                                                                                                   |
|Version      |v0.3                                                                                                                                                                                                                 |
|DateIssued   |07.07.2017                                                                                                                                                                                                           |
|DateModified |NA                                                                                                                                                                                                                   |
|Definition   |Recommended best practice is to use a controlled vocabulary such as the Getty Thesaurus of Geographic Names.                                                                                                         |
|Comment      |Examples: "Germany", "Denmark", "Colombia", "España". For discussion see http://terms.tdwg.org/wiki/dwc:country;  This should be added if a more precise location is unavailable, to enable data to be used by GBif. |
## `countryCode`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#countrycode)

|             |countryCode                                                                                                                                                                                                                            |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |factor                                                                                                                                                                                                                                 |
|vocabulary   |                                                                                                                                                                                                                                       |
|Identifier   |                                                                                                                                                                                                                                       |
|Refines      |http://rs.tdwg.org/dwc/terms/countryCode                                                                                                                                                                                               |
|Replaces     |NA                                                                                                                                                                                                                                     |
|Version      |v0.3                                                                                                                                                                                                                                   |
|DateIssued   |07.07.2017                                                                                                                                                                                                                             |
|DateModified |NA                                                                                                                                                                                                                                     |
|Definition   |The standard code for the country in which the Location occurs. Recommended best practice is to use ISO 3166-1-alpha-2 country codes.                                                                                                  |
|Comment      |Examples:"DE" for Germany, "AR" for Argentina, "SV" for El Salvador. For discussion see http://terms.tdwg.org/wiki/dwc:countryCode; This should be added if a more precise location is unavailable, to enable data to be used by GBif. |
## `occurenceRemarks`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#occurenceremarks)

|             |occurenceRemarks                                                                                   |
|:------------|:--------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                          |
|vocabulary   |                                                                                                   |
|Identifier   |                                                                                                   |
|Refines      |http://rs.tdwg.org/dwc/terms/occurrenceRemarks                                                     |
|Replaces     |NA                                                                                                 |
|Version      |v0.3                                                                                               |
|DateIssued   |07.07.2017                                                                                         |
|DateModified |NA                                                                                                 |
|Definition   |Comments or notes about the Occurrence.                                                            |
|Comment      |Example: "found dead on road". For discussion see http://terms.tdwg.org/wiki/dwc:occurrenceRemarks |

# Extension: Biodiversity Exploratories

This section records location in the context of the exploratories. From `ExploratotriesPlotID` a detailled georeference can be inferred. Additional spatial resolution, e.g. on subplots, may be provided in `locationID` of section sampling event. 

## `OriginExploratories`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#originexploratories)

|             |OriginExploratories                                                                         |
|:------------|:-------------------------------------------------------------------------------------------|
|valueType    |logical                                                                                     |
|vocabulary   |TRUE;FALSE                                                                                  |
|Identifier   |                                                                                            |
|Refines      |                                                                                            |
|Replaces     |NA                                                                                          |
|Version      |v0.3                                                                                        |
|DateIssued   |07.07.2017                                                                                  |
|DateModified |NA                                                                                          |
|Definition   |Did measured specimens originate from Exploratories Plots? TRUE or FALSE, defaults to FALSE |
|Comment      |As unambiguous flag for data and specimens that are originating from Exploratories sites.   |
## `ExploratoriesPlotID`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#exploratoriesplotid)

|             |ExploratoriesPlotID                                                                                                                                                                                                                                                                                                                              |
|:------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |factor                                                                                                                                                                                                                                                                                                                                           |
|vocabulary   |                                                                                                                                                                                                                                                                                                                                                 |
|Identifier   |                                                                                                                                                                                                                                                                                                                                                 |
|Refines      |                                                                                                                                                                                                                                                                                                                                                 |
|Replaces     |NA                                                                                                                                                                                                                                                                                                                                               |
|Version      |v0.3                                                                                                                                                                                                                                                                                                                                             |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                                                                       |
|DateModified |NA                                                                                                                                                                                                                                                                                                                                               |
|Definition   |EP plot ID (or also any valid Gridplot ID or VIP ID) where the measured specimen was extracted. Only for specimen that were extracted from the exploratories directly (or direct offspring, if hatched in the lab). Please also report it, even if this was not part of your research question and provide a Date (a year at last) if available. |
|Comment      |                                                                                                                                                                                                                                                                                                                                                 |
## `Exploratory`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#exploratory)

|             |Exploratory                                                                                                                                                            |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |factor                                                                                                                                                                 |
|vocabulary   |HAI; SCH; ALB                                                                                                                                                          |
|Identifier   |                                                                                                                                                                       |
|Refines      |                                                                                                                                                                       |
|Replaces     |NA                                                                                                                                                                     |
|Version      |v0.3                                                                                                                                                                   |
|DateIssued   |07.07.2017                                                                                                                                                             |
|DateModified |NA                                                                                                                                                                     |
|Definition   |Exploratories Region (Hainich, Schorfheide, Alb) for sorting purpose and readability, or if exact Plot ID is not available. Report the Region in format: HAI; SCH; ALB |
|Comment      |                                                                                                                                                                       |
## `ExploType`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#explotype)

|             |ExploType                             |
|:------------|:-------------------------------------|
|valueType    |factor                                |
|vocabulary   |W; G                                  |
|Identifier   |                                      |
|Refines      |                                      |
|Replaces     |NA                                    |
|Version      |v0.3                                  |
|DateIssued   |07.07.2017                            |
|DateModified |NA                                    |
|Definition   |W for forest or G for grassland plot. |
|Comment      |                                      |

# Metadata vocabulary

These data are required when combining datasets from different sources. We suggest integrating a `datasetID` referencing to an external data sheet or adding columns to the dataset to keep important information about authorship and terms of use at the measurement level. 


## `rightsHolder`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#rightsholder)

|             |rightsHolder                                                                             |
|:------------|:----------------------------------------------------------------------------------------|
|valueType    |character                                                                                |
|vocabulary   |                                                                                         |
|Identifier   |                                                                                         |
|Refines      |http://purl.org/dc/terms/rightsHolder                                                    |
|Replaces     |NA                                                                                       |
|Version      |v0.3                                                                                     |
|DateIssued   |07.07.2017                                                                               |
|DateModified |NA                                                                                       |
|Definition   |A person or organization owning or managing rights over the resource, i.e. this dataset. |
|Comment      |A list of author names (separated by &#124;) or name of a consortium, or institution     |
## `bibliographicCitation`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#bibliographiccitation)

|             |bibliographicCitation                                                                                                                                                                                                                                                                                            |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                                                                                                                                        |
|vocabulary   |                                                                                                                                                                                                                                                                                                                 |
|Identifier   |                                                                                                                                                                                                                                                                                                                 |
|Refines      |http://purl.org/dc/terms/bibliographicCitation                                                                                                                                                                                                                                                                   |
|Replaces     |NA                                                                                                                                                                                                                                                                                                               |
|Version      |v0.3                                                                                                                                                                                                                                                                                                             |
|DateIssued   |07.07.2017                                                                                                                                                                                                                                                                                                       |
|DateModified |NA                                                                                                                                                                                                                                                                                                               |
|Definition   |A bibliographic reference for the resource as a statement indicating how this record should be cited (attributed) when used. Recommended practice is to include sufficient bibliographic detail to identify the resource as unambiguously as possible.                                                           |
|Comment      |e.g. "Gossner, M.M., Simons, N.K., Achtziger, R., Blick, T., Dorow, W.H.., Dziock, F., et al. (2015). A summary of eight traits of Coleoptera, Hemiptera, Orthoptera and Araneae, occurring in grasslands in Germany. Sci Data, 2, 150013, doi:10.1038/sdata.2015.13" If dataset has been published, include DOI |
## `license`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#license)

|             |license                                                                                                                                                                                   |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                                                                                 |
|vocabulary   |                                                                                                                                                                                          |
|Identifier   |                                                                                                                                                                                          |
|Refines      |http://purl.org/dc/terms/license                                                                                                                                                          |
|Replaces     |NA                                                                                                                                                                                        |
|Version      |v0.3                                                                                                                                                                                      |
|DateIssued   |07.07.2017                                                                                                                                                                                |
|DateModified |NA                                                                                                                                                                                        |
|Definition   |A legal document giving official permission to do something with the resource.                                                                                                            |
|Comment      |Examples: "http://creativecommons.org/publicdomain/zero/1.0/legalcode", "http://creativecommons.org/licenses/by/4.0/legalcode". For discussion see http://terms.tdwg.org/wiki/dwc:license |
## `datasetID`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#datasetid)

|             |datasetID                                                                                                                      |
|:------------|:------------------------------------------------------------------------------------------------------------------------------|
|valueType    |character                                                                                                                      |
|vocabulary   |                                                                                                                               |
|Identifier   |                                                                                                                               |
|Refines      |http://rs.tdwg.org/dwc/terms/datasetID                                                                                         |
|Replaces     |NA                                                                                                                             |
|Version      |v0.3                                                                                                                           |
|DateIssued   |07.07.2017                                                                                                                     |
|DateModified |NA                                                                                                                             |
|Definition   |An identifier for the set of data. May be a global unique identifier or an identifier specific to a collection or institution. |
|Comment      |e.g. BExIS ID, or  a DOI referring to the published dataset                                                                    |
## `datasetName`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#datasetname)

|             |datasetName                                                          |
|:------------|:--------------------------------------------------------------------|
|valueType    |character                                                            |
|vocabulary   |                                                                     |
|Identifier   |                                                                     |
|Refines      |http://rs.tdwg.org/dwc/terms/datasetName                             |
|Replaces     |NA                                                                   |
|Version      |v0.3                                                                 |
|DateIssued   |07.07.2017                                                           |
|DateModified |NA                                                                   |
|Definition   |The name identifying the data set from which the record was derived. |
|Comment      |e.g. a BExIS dataset name, a unique name for the traitdataset        |

# Terms for Traitlists (a 'Trait Thesaurus')

Ontologies for functional traits are beeing developed for different organism groups, mostly centered around certain research questions or subjects of study. To date, the TRY database takes the most inclusive approach on functional traits for vascular plants (Kattge) and describes XX traits and put them into the hierarchical structure of an ontology.

For some animal groups, similar approaches do exist, but few are available as an online ontology. 

As a starting point for creating an ontology for functional traits, we propose the following terms for trait lists (also termed 'lookup tables' of traits, or trait 'Thesaurus'), to describe functional traits that are in the focus of a single research project. Those trait lists would be uploaded along with the trait dataset. 

Using this standardized terminology will allow merging trait definitions from multiple sources. We encourage providing these lookup tables as an open ressource on public ontology and terminology servers, to enable a global referencing. 

## `valueType`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#valuetype)

|             |valueType  |
|:------------|:----------|
|valueType    |           |
|vocabulary   |           |
|Identifier   |           |
|Refines      |           |
|Replaces     |NA         |
|Version      |v0.3       |
|DateIssued   |07.07.2017 |
|DateModified |NA         |
|Definition   |           |
|Comment      |           |
## `FactorLevels`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#factorlevels)

|             |FactorLevels |
|:------------|:------------|
|valueType    |             |
|vocabulary   |             |
|Identifier   |             |
|Refines      |             |
|Replaces     |NA           |
|Version      |v0.3         |
|DateIssued   |07.07.2017   |
|DateModified |NA           |
|Definition   |             |
|Comment      |             |
## `MaxAllowedValue`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#maxallowedvalue)

|             |MaxAllowedValue |
|:------------|:---------------|
|valueType    |                |
|vocabulary   |                |
|Identifier   |                |
|Refines      |                |
|Replaces     |NA              |
|Version      |v0.3            |
|DateIssued   |07.07.2017      |
|DateModified |NA              |
|Definition   |                |
|Comment      |                |
## `MinAllowedValue`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#minallowedvalue)

|             |MinAllowedValue |
|:------------|:---------------|
|valueType    |                |
|vocabulary   |                |
|Identifier   |                |
|Refines      |                |
|Replaces     |NA              |
|Version      |v0.3            |
|DateIssued   |07.07.2017      |
|DateModified |NA              |
|Definition   |                |
|Comment      |                |
## `MeasurementTypeDescription`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#measurementtypedescription)

|             |MeasurementTypeDescription |
|:------------|:--------------------------|
|valueType    |                           |
|vocabulary   |                           |
|Identifier   |                           |
|Refines      |                           |
|Replaces     |NA                         |
|Version      |v0.3                       |
|DateIssued   |07.07.2017                 |
|DateModified |NA                         |
|Definition   |                           |
|Comment      |                           |
## `Comments`  
[go to top](http://fdschneider.de/bexis_traits/traitdatastandard.html)  |  [direct link](http://fdschneider.de/bexis_traits/traitdatastandard.html#comments)

|             |Comments   |
|:------------|:----------|
|valueType    |           |
|vocabulary   |           |
|Identifier   |           |
|Refines      |           |
|Replaces     |NA         |
|Version      |v0.3       |
|DateIssued   |07.07.2017 |
|DateModified |NA         |
|Definition   |           |
|Comment      |           |

----

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">Ecological Traitdata Standard </span> by <span xmlns:cc="http://creativecommons.org/ns#" property="cc:attributionName">Florian D. Schneider, Nadja Simons, Caterina Penone, Andreas Ostrowski</span> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.

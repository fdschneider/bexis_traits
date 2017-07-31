---
title: "Introducing an Ecological Trait-data Standard"
author: "Florian D. Schneider, Nadja K. Simons, Andreas Ostrowski, Caterina Penone"
output:
  pdf_document: default
  word_document: default
fontsize: 12pt
header-includes:
- \usepackage{lineno}
geometry: margin=1.5in
---

\linenumbers

<!-- 
The aim of the methods paper is to 
- highlight the importance of data standards for functional traits
- provide standards and tools for decentralised implementation

# Introduction

1. importance of trait based ecology, current research questions, current applications of traits. 
2. Overview of existing database initiatives. Offering access management and harmonization;

(table 1 listing of open an restricted trait databases and datasets)

3. Heterogeneity of data standards and centralised databases. Open Access, publication in low-threshold data repositories becomes more important. Decentralisation of databases and importance of data brokering requires data standards. 
- lack of a universal traitdata standard. 

## Common structure of trait datasets

1. minimal definition of a trait dataset
2. possible data formats: matrix, occurence table, measurement long table 
- species--trait matrix is common for sharing taxon-level averages or facts, common for publishing species-level data and literature data. but not raw-data. The means of obtaining the average are intransparent and may be biased by local conditions. 
- occurence table is common for empirical replicated measurements of traits, raw data. Ideal for correlation analysis of traits. Also, multivariate traits, e.g. morphometric landmarks or biochemical trais. Not ideal for merging data from multiple sources. 
- measurement table, longtable: ideal for raw data. Machine readable, simple to standardize and for sharing data, merging and combining data. 
- additional information may apply to different layers: on measurement or occurence, co-variate analysis, environmental filters, spatial distribution. 

(figure 1 species-trait matrix plus additional information, vs longtable plus additional information )

# Towards an Ecological Traitdata Standard

1. definition of structure: longtable format is most feasible to carry information at measurement level, link to external datasets via globally unique identifiers (or dataset specific)
- add occurence level information (e.g. location, sex) and measurement level (e.g. aggregated data, statistics) information
- apply taxon name standardization
- apply trait standardization, link to definitions (trait lists, thesaurus) via globally unique identifiers, semantic network; apply unit and factor level harmonization

## A glossary of terms

- We provide: Glossary of terms for trait data and trait definitions

(table 2: most relevant terms of the traitdata standard, scheme of a term definitition)
(table 3: terms for trait definitions / trait lists)

## Computational tools for producing compliant data

- R package traitdataformat
- standardize and harmonize trait data for publication
- merge, split, apply trait data of different sources 

(figure 2 process chart from original file to standardized output)

# Discussion

- With these tools, traitdata will be easier to harmonize 
- decentralised structures, not limited by infrastructural projects
- open source community development, invite contributions to traitdata standard and toolchain of R-package
- encourage development of trait definitions and semantic ontologies
- a global analysis of ecological traits will be facilitated 

-->

# Introduction

*< importance of trait based ecology, current research questions, current applications of traits. >*

Functional traits are phenotypic characteristics that are related to the fitness and performance of an organism. [@Mcguill06; @Violle07]

Traits can be measurements of organism morphology, life-history characteristics such as reproductive strategies, physiological traits including metabolism and photosynthetic activity, feeding traits, biochemical and isotopic compounds, behavioural traits, as well as environmental traits. 

A focus on functional traits allows ecologists to describe the role of a species in an ecosystem or its ability to persist under certain environmental conditions. 
<!-- Malte: Correct, but given the extensive list of what traits are useful / used for that is given in the next paragraph, this sentence suggests a too narrow scope of what traits are useful for. I would probably delete it and move the response / effect traits sentence further down. -->
Some studies differentiate effect traits and response traits (or performace and fitness traits), depending on the research question. 

Reflecting this wide range of measures and approaches, traits are assessed with a variety of research questions in mind. 

Traits help in bridging individual level behaviour and physiology into processes at the ecosystem scale (@Diaz2013). The analysis of correlations between traits and intraspecific variation informs about the physiological and evolutionary trade-offs and helps to identify economic strategies of organisms beyond taxonomy (@Menezes2010)  (@Forister2015). 
Inferring the unknown trophic role and ecological function of individuals from their apparent features (@Duarte2011, @Fontaine2006) is a promising venue to bypass taxonomic impediment, the fact that a majority of species are yet undescribed and have not been observed in the ecosystem. 
Looking at community weighted means and variance of functional traits, researchers aim to understand changes in functional composition or the loss of functional diversity and ecosystem services (@Wood2015) in consequence to global change or local anthropogenic land use (environmental filtering; @Hopfenmuller2014, @Jennings2009, @Moretti2013). (@deBello2011) (Gossner et al, other Explo papers) 

Traits  allow comparision across trophic levels. However, a multi-trophic integration is difficult because of different standards, methods, and functional focus. A harmonization of trait data standards across functional groups would be of huge benefit for a multi-trophic understanding of ecosystems. 
<!-- Malte: Why is a multitrophic perspective beneficial / necessary? This point needs to be clearly made here. -->

Functional ecology has grown into a major field in ecological research!
A global synthesis of traits brings major insights in ecosystem processes and ecosystem services, enables projections in future climate and land use scenarios. Traits link ecological research to evolution, and management (functions and services) for biodiversity conservation (land use intensification), climate research (environmental filters). It is thus an interdisciplinary/cross-topic field with great potential. 

<!-- 

Refer to Kattge et al 2011, Violle et al 2007, Diaz et al 2007, McGill et al. 2006, Aubin et al. 2013, Lavorel et al. 2002...
## trait-based research within the Biodiversity Exploratories

Refer to successfully published papers on arthropod traits, multi-trophic trait variation etc. 

Allan et al 2015
Boerschig et al 2013
Gossner et al 2015 & 2016
Simons et al 2014 & 2016
Kühsel et al 2015 & 2016
Birkhofer et al 2015
Chisté et al 2016
Gamez-Virues et al 2015

Summarize different questions, currently proposed in above- and below ground work within the Exploratories, focus on plant traits, arthropod traits, microbial traits.

Need to unify for multi-trophic integration

Trait matching integrates function across trophic levels, influence of land use and environmental filtering on trait composition, Exploratories are ideal framework for testing

-- Cat: here I would organize a bit differently to link better to the previous section:--
Traits can bridge biodiversity and functioning and that they allow comparision across trophic levels. Furthermore trait composition is influenced by land use and environmental filtering of traits. 
Exploratories are ideal framework for testing these questions because they are framed to study interactions between LUI, biodiversity and functions. 
However, multi-trophic integration is difficult because of different standards, methods, focus..
 needs unification in order to advance research and make data use possible for future generations

<!-- Nadja: I like Caterinas suggestion --> 
<!-- Flo: Yes, makes sense. -->
<!-- Malte: I agree, Caterina's suggestion makes it easier to follow for the reader. -->


*< Overview of existing database initiatives. Offering access management and harmonization >*

For many organism groups and research questions, trait data have been standardised into databases. Most prominently, plant traits from many different sources have been collated into the quickly growing TRY databse. TRY combines trait data from other published databases with individually owned datasets and provides an extended access management and data query services. Other more specialised databases for plant traits exist, for instance for root measurements (refs and URLs). 
In the animal kingdom, a wealth of trait-databases has been created that covers different organism groups or interaction types or ecosystems. 
<!-- Malte: ... or ecosystems. However, a unified framework to standardize these approaches is still lacking. (needs something like this, otherwise it introduces plant traits and TRY , but for animals stops at: there are many data sets here, too.) -->
Besides these harmonized databases, an unknown plethora of single datasets has been published along with article publications over the past decades. As an attempt to track these unstandardized datasets, we initiated a living spreadsheet registry which invites submissions of any open data (Google Spreadsheet link, table 1).

(table of existing databases? name, url, focus, number of records, openness of data, maintained by)

<!-- Caterina: I like this table idea but should we limit it to plants and arthropods or also other organisms? Europe or whole world? I would opt for plants and arthropods in Europe but in case this becomes a publication open a collaborative file where anybody in the world can add the information for any organism in any part of the world. 

Flo: I like this idea of starting a collaborative list on trait datasets. This
   1. illustrates the hetereogeneity of trait data and the need for a traitdata standard
   2. encourages a global traitdata analysis based on heterogeneous sources, which is enabled by the tools we provide here. See https://github.com/fdschneider/bexis_traits/issues/20
   -->

*< Heterogeneity of data standards and centralised databases >*

It becomes apparent, that all databases come with their own structure, reflecting the research questions of the initiatives behind them and their organismal focus. A harmonization of traits can be achieved by services like TRY, which take a huge effort to attract data submissions and map them into a common scheme. 

Furthermore, these databases provide access management services and tracking of data usage in studies and secondary publications. Mandatory Open Access publication still seems to prevent some data providers from uploading their data, why many databases encourage a permissive data policy but do not enforce it. 
<!-- Malte: I think this definitely needs to be backed up with a reference. -->

Centralised databases like TRY experience rapid growth but are at some point reaching a resource limit in personnel and funding.

Public research funding agencies increasinly demand the publication of data without access restrictions [@swan12; @allison15], but not all scientific databases for functional traits are enabled to comply with this standard. The training on compliance with open data standards within the community of environmental sciences can still be much improved [@schmidt15]. 

Data brokering services such as the German Federation on Biological Data (gfbio.org) are aiming to ease data publications and standardization for researchers, for instance by providing terminologies and ontologies for environmental data. 
Such ontologies are being developed for plant traits, for instance in the TOP Thesaurus of plant traits that is used for the TRY database. On the side of animal traits, few initiatives published comprehensive trait standards and method catalogues, like for instance [@moretti16, betsi]. 
<!-- Malte: What about Moretti et al 2017 Funct Ecol: Handbook of protocols for standardized measurement
of terrestrial invertebrate functional traits? -->
Today, several biodiversity data intitiatives are striving for a global integration of ecological and biological information and develop universal data frameworks for trait data. The EOL TraitBank for instance is the most general framework to date (Parr et al 2015) and suggests wrapping trait data into structured Darwin Core Archives.

However, the publications in low-threshold data repositories such as figshare, datadryad, researchgate or zenodo are gaining importance and foster a decentralised data hosting with low expectations regarding data standardization and documentation. Given this prospect, there will be no lack of data, but a lack of data standardization. 

With this paper, we propose a roadmap towards a comprehensive trait data standard, based upon the considerations by Parr et al. with the combined perspectives of empirical biodiversity researchers (data providers), biodiversity synthesis researchers (data users), and biodiversity informatics researchers (data managers).   

## Common structure of trait datasets

As a minimum consensus, trait datasets may be defined as follows: 
A trait-dataset contains quantitative measurements or qualitative facts (i.e. trait values) <!-- Cat: the difference is not totally clear to me - is it the difference between field vs literature gathered data?  Flo: I see measurements as quantitative and facts as qualitative traits, which mostly aligns with field vs. literature, but not entirely.  -->  about physical phenotypic characteristics of fitness, behaviour or performance (i.e. traits) of individuals (or parts of an individual) assigned to an entity of a biological taxon (i.e. a species or higher taxon). The entity or observation (i.e. the occurence) to which the reported measurement or fact applies may differ in resolution -- depending on the scientific question -- and could be a subsample or bodypart, an individual specimen, an entire species or higher-level taxon. 

*< standardised reference to taxon names >*

To obtain comparability in biodiversity data, much effort has gone into the development of precise definitions and standardised reference lists of taxon names. (References)

In order to allow for a maximized knowledge gain and scientific benefit of obtained trait data, authors and data managers must provide compatibility to other datasets by referencing their data to published taxonomic ontologies, which exist for all organism groups and many regions of the world (examples!). Widest coverage today may be found in the GBIF backbone taxonomy or ... <!-- Nadja: would FaunaEuropeae be another example? Flo: Yes, it seems to be used frequently by german community as a reference, right? However, their ontology is not really machine readable, or how does it work in practice? -->. Compatibility with these ontologies is achieved by referencing an observation to a unique identifier (which can be either alpha-numeric or full taxon name, including author and date of first description, or an unambiguous Unique Resource Identifier, URI, which refers to a precisely defined term in a published ontology) and providing the information which ontology the taxon names refer to in the metadata.

*< standardized reference to trait definitions >*

Similarly motivated, traits for target organism groups and ecosystems have been categorized and defined in thesauri (e.g., TOP Plant Trait Ontology or Vertebrate Trait Ontology [28]) or ontologies (morphometrics?), which also provide unique identifiers for referencing along with more or less precise definitions of the body measures, morphometric landmarks, categorical traits or environmental conditions, for instance. 
Multiple approaches have spawned around the initialisation of trait databases, most advanced certainly for plant traits in the TRY database and its reference Thesaurus of Plant characteristics (TOP).  

Traits are not only defined in terms of their interpretation, but are ideally also standardised in terms of numerical units and, even more important, the use of factor levels. This is challenging given the range of data types that fall within datasets of functional traits. 
Numerical values represent measurements of length, volumes, ratios, rates or timespans. Integer values may apply to count data (e.g. eggs per clutch). 
Binary data (encoded as 0 or 1) or logical data (coded as TRUE or FALSE) may apply to qualitative traits such as specific behaviour during mating (e.g. are territories defended) or specialisation to a given habitat (e.g. species restricted to relicts of primeval forests). Many traits are categorical and allow for a constrained set of factor levels, such as sex differences in wing morphology (both sexes winged, both sexes unwinged, only males winged, only females winged) or unconstrained entries such as color. Categorical traits often are ordinal, i.e. they have a logical sequence as in the case of life stages or hibernation stages, or habitat preference traits such as horizontal stratum use. 
Finally there are specific formats of multivariate trait values, e.g. x.y.z coordinates of a landmark measured in 3D space or relative abundance of chain-lengths in biochemical compounds.
Handling this multitude of value types in heterogeneous databases is challenging and requires an unambiguous trait definition. 

To achieve comparability of traits across taxonomic groups, some trait standards suggest a hierarchical classification or a relational tree of functional traits (e.g. TOP or T-SITA). Each trait definition may link to a broader or narrower term. For instance, the definition of 'femur length of first leg, left side' is narrower than 'femur length' which is narrower than 'leg trait' which is narrower than 'locomotion trait'. (Ref semantic database methods)
This links traits of similar functional meaning and allows cross-taxon comparative studies at the level of broader terms. 
Thus, a trait thesaurus would assign trait names with A) a unique definition and B) an expected format of measured values or reported facts, and might additionally provide C) a hierarchical or tree-based classification of traits. 

Initiatives to standardise traits into consensus terminology are usually formed around a specific research question, methodology, or organism group and therefore vary in the traits that they consider important. To make trait measurements truly comparable, it requires precise definitions of traits, including the expected numerical or categorical resolution and measurement units. These reference definitions are currently being published in methodological handbooks (Moretti et al , ) or lists of accepted traits (databases), or an online ontology or thesaurus (TOP, T-Sita, ). The latter is the only option that enables direct linking to a term via a URI.
Some trait glossaries extend into (machine readable) ontologies by providing a hierarchical or tree-based classification of traits (TOP, Moretti et al) . These systematic approaches to traits will be very useful for comparing similar traits measured in different taxa at higher hierarchical levels. The benefit of such classifications will increase if API services provide a systematic way to extract the higher-level trait hierarchies. 
To our knowledge, none of the trait initiatives today provides a fully open API that would allow extracting machine readable definitions and terms via software tools. To harmonize trait data across databases, future trait standard initiatives should provide this functionality.  


*< data structure >*

Such trait-datasets take different formats. For instance, if trait data have been collated at the species level from different literature sources or from expert knowledge, they usually are reported in a species $\times$ trait matrix format, with a column of trait values for each trait recorded and a row for each species (or taxon) for which data were available. This format is usually reporting missing data as NA. It may store additional information (e.g. on variation of means or literature source) in secondary colums. The matrix format is widely used for the production of lookup-tables at the species level, which for instance may be used for the calculation of community weighted means or functional diversity metrics at the community level (Refs). Also, missing information about the behaviour and functional role of species of little ecological record may be inferred from these tables (Refs).

For investigations of within--species-variation of traits, traits would be recorded per observation, i.e. each individual specimen would be recorded in a row, with the traits measured on it stored in columns. Those data are common in investigations of evolutionary trade-offs and trait correlation, or of intra-specific variation and sexual dimorphism. We term these tables as occurence data tables, since each row is centered around a single physical occurence of a species. This format is the most intuitive for recording own empirical measurements and therefore is common for measured data and rarely found for reported facts obtained from the literature.

Computationally most effective and allowing for highest flexibility is the storage of traitdata in long-table formats, where each row is reserved for a single measurement or fact of a specific trait, referenced to a single occurence (i.e. a specimen) assigned to a taxon. This allows for repeated measurements, even on a single individual. Also, multivariate trait measurements can be recorded in this format by linking multiple rows via a unique measurement ID. 
The latter format is therefore providing the highest resolution and ideal for storing raw data of trait measurements in huge databases and link them via the respective unique identifiers to additional information, such as occurenceID or locationID.  

*< co-variates and additional information >*

In addition to the minimal definition above, trait-datasets may come with a variety of additional information. The long-table format is ideal for storing this metadata-information on the measurement level. Additional information on the occurence (i.e. the specimen where the trait was measured), the measurement method or accuracy (for instance detailed information on climate, habitat or soil conditions) can easily be added as columns in the datasheet. They could also be referenced in other sheets of a database and linked via unique IDs. The matrix or table format would have to keep this information referenced in metadata or linked datasets. 

(We conceptualize trait-datasets to  not include information about a species' interaction partners/associations of an organism, since they are -- to our understanding -- not within the scope of functional traits. However, such network data may be of interest to be combined with trait data. )

<!-- Cat: here I guess that a figure showing few rows of a species x trait matrix and a long-format one with links to other information (metadata,..) woud help quite a lot. By experience some users are not be familiar with the interest of using the long-table format.-->

*< additional detail on measurement or fact >*

Data resolution differs and researchers might report aggregated species averages or replicates of individual measurements. A universally applicable framework needs to fall back to the smallest unit, i.e. the single measurement (Kattge  et al 2011), and allow multiple measurements of a single trait for a single species at a single site (i.e. one observation). Indeed this resolution is necessary for assessing intra-specific trait variation, or even variation of traits of a single specimen (e.g. size of leaves of a single tree).  In case of aggregated measurements, however, researchers might record the average and the dispersion, and also keep information about the statistical method of an average record and the dispersion metric (e.g. variance or range) as well as the number of individuals aggregated. Having this information available, would allow compiling weighted averages of species traits by combining data of different resolution.

In the case of measured data, the method and accuracy of measurement, the methods of sampling or preservation of the specimen, as well as the person measuring, would be recorded to assess any methodological bias.
The measurements most likely were taken under certain natural or artificial environmental conditions, that might also be recorded along with the trait data. A protocol of measurement might be referred to. 

In case of datasets collating information from other sources, literature would be referenced or an expert name reported. For museum specimens or private collections, the unique identifier of the museum collection would link the measurement to a real physical object.

(Many of the information described in the previous two section are defined in the [Darwin Core Extension Measurement or Fact](). )

*< additional information on observation context /occurence level information >*

The entity at which the measurement was obtained or to which it refers to may be further detailed: Some traits are recorded as species or population level averages, such as functional guild assignment or average longevity. In that case, the taxon rank to which the measurement applies needs to be documented. 
Similarly, measurements might resolve to lower than species level, to subspecies, or even sub-groups of a single species, like a sex, caste, or morphotype. 

Trait data may be recorded from specimens which developed in a particular spatial and climatic context, or were cultivated under (semi-)controlled conditions. A dataset should report these details.  

Therefore, georeference, altitude and date of sampling would be recorded to capture and investigate climate and location as a source of trait variation. A unique location identifier may link the observation to an experimental context or dataset-specific reference table or a global database of locations. To add ecological context, the habitat type where the specimen was observed could be classified.

(Most of the information described in the last two sections are subsumized under the [Occurence Extension of the Darwin Core](http://tools.gbif.org/dwca-validator/extension.do?id=http://rs.tdwg.org/dwc/terms/Occurrence#Occurrence), and may also be referenced into an external database via a unique Occurence identifier. ) 

*< information on attribution and permissions to use >*

Finally, there is the set of information that applies to the entire trait-dataset, which classifies them as metadata. Since trait data are of great use for synthesis studies, information about how the data may be distributed, re-used and attributed to are of particular importance for trait datasets. Most researchers encourage re-use of their published datasets while making sure they are sufficiently credited. The use of permissive licenses for traitdata publications, such as Creative Commons Attribution or Creative Commons Zero/Public Domain release, has been established as the gold standard. 

<!-- Where is this data record available online? Source in the Measurements or Facts extension file is for a url to be displayed alongside the data point, so EOL visitors can click through to an online resource where the data originated. This might be a dataset stored at an online repository, a taxon page on a website, or any other online location.
What shall I cite if I use this data record in a publication? BibliographicCitation in the Measurements or Facts extension file is for the suggested citation format for a user of this dataset to include in a references list or bibliography. Even if the data record or dataset have never been published elsewhere, we recommend that you craft an appropriate citation so others can provide proper credit.
If the dataset is from a literature review, and one or more references are available for individual data points, these references should be recorded in the References extension and listed by their Reference IDs in the ReferenceID field of the Measurements or Facts extension file, see below.  -->

# Proposing an ecological traitdata standard 

In this paper, we propose a universal scheme of defined column names and data structure that captures the different degrees of resolution and measurement detail for multiple use cases of trait data. We also provide computational tools in an R package to help users to format their original data into the proposed scheme.

Existing initiatives for standardising data are focused on a constrained organism group, ecosystem type or region and compile data in own centralised databases. Among the different approaches, the TRY database for plant characteristics is certainly the one with highest coverage. The most inclusive trait database to date has been created in the framework of the Encyclopedia of Life (EOL) with TraitBank (Parr et al 2015). With the framework presented here, we aim for compatibility with those standards.

However, while TraitBank and TRY are centralised infrastructures, we want to facilitate the use of a standard format of trait data by suggessting a flexible formatting scheme that can be applied in multiple contexts, for instance of a taxon-specific database or in user-side compilations of trait data from different sources. 

For standardisation and comparability of traitdata across datasets, conventions on trait definitions and taxon names are inevitable. We consider the fact that most authors have their own schemes for standardisation and may contribute to different communities by allowing for a double record of both user-specific and standardised entries (TRY, Kattge et al ).  

The trait-dataset may be linked to supporting information (e.g. on the occurence, the methodology, the original source, the sampling event or location) on the metadata level or in attached data tables, e.g. in the form of a Darwin Core Archive, or into external databases via URIs. For this interlinkage with other datasets, columns are reserved for unique identifiers (e.g. linking measurements to location, collections, literature) that refer to a dataset-specific or globally defined ID. (#Cat: should it be one or the other?)

In the subsequent sections we propose a set of columns that compose a trait dataset, starting with the ones required for our minimal definition of trait-datasets proposed above and continuing with columns that add information on the level of the occurence, the measurement or fact, and the entire record. We build upon the structure proposed by Parr et al for the TraitBank database, which uses field definitions of the Darwin Core standard (DWC). We expand the definitions of these fields for the use case of trait data and add further field definitions, to cover the special demands of trait-based research. See table 2 for a full description of the column names and the reference URI. 

(table 2: most relevant terms of the traitdata standard, scheme of a term definitition)
(table 3: terms for trait definitions / trait lists)

## minimal requirement of a trait-dataset

For the minimal definition of trait-datasets, the central content of a row is the reported measurement or fact for a single observation, which is composed of a value (`traitValue`) and -- for numeric values -- a standard unit (`traitUnit`).
To link the measurement or fact to a clear trait definition, a unique identifier links each row to a trait name defined by a given lookup-table (`traitType`) and a globally unique identifier of the measurement type, a trait ID (`traitID`). 
 
The core data are also keeping a record of the scientific taxon for which the measurement or fact was obtained via globally accepted identifiers. To provide an unambiguous reference which is easy to read for researchers and for software, this identifier is provided in the form of an unambiguous taxon name (`scientificName`) as well as a machine readable ID (`taxonID`). 


Further unique identifiers link the row to a single specimen or occurence (`occurenceID`), which can be described with further detail in a separate data table or the same table using the columns provided in the occurence extension detailed below. This identifier is usually dataset-specific and can be defined by the author. Some data-types may use global identifiers for occurence data, e.g. a GBIF URI or a museum collection code that is publicly available.

Similarly, each single measurement (i.e. each row of the dataset, except for multivariate traitdata; see below) is labelled by a unique identifier (`measurementID`) and receives further detail in a linked dataset or in the same dataset using the columns provided by the measurement or fact extension. 

To enable compatibility of the dataset with other datasets, we propose to add a second set of columns that contain standardized entries of the taxon name (`scientificNameStd`) that maps synonyms to an accepted species name according to a published taxonomic ontology (e.g. GBIF Backbone Terminology) and links to it using a globally unique identifier (`taxonID`). Similarly, the trait dataset should map trait names (`traitNameStd`) and harmonize reported values (`traitValueStd` and `traitUnitStd`) according to a published trait list (a thesaurus). 
This dupliation of data enables continuity on the authors side and quality checking and comparability on the data users side. 

Additionally, metadata should contain information about the authorship and ownership of the data and the terms of use. These information may be kept in the metadata of the dataset, but if datasets from different sources are merged, those should be referred to by a unique identifier (`datasetID`) or be reported as additional columns in the merged dataset (`author`, `license`, ...; see Dublin Core Metadata standards, Ref). 

In the following paragraphs, we provide a suite of extended column definitions that capture the important aspects of the various types of trait-data. 

(Table showing example of minimal data)
(#Cat I find the sections below very clear but they in part repeat things alredy mantioned in the present section. I would move this "minimal content" section after the definitions so the columns are defined just once and the lenght/complexity reduced.)

<!-- ## globally unique identifier of a measurement

To ensure compatibility of datasets of different origin, we propose to use a cryptographic hash function for the generation of a globally unique identifier of each measurement (`measurementID`). Cryptographic hash functions compile strings of variable content length into a bit string of fixed size. This string can be used to compare data and check for duplicates across multiple datasets. The method we propose is to collate a comma separated string of all original (i.e. user provided, labelled with  `_original`) data columns and parse them using the SHA1 algorithm. The rationale of using the user-specific columns only is that those data are not changing even if a measurement has been reformatted for a different context.  We provide a script to create the measurementID as well as a automated workflow in the R package described below. -->

*< global taxonomy standards >*

The entries provided in the fields `scientificName` and `taxonID` are supposed to refer to an accepted and published taxonomic ontology. Any synonyms should be mapped to the accepted scientific names. The most complete taxonomic terminology service that is reachable through an API and software tools is the GBIF backbone taxonomy. The function `getGbifTaxonomy()` provided within the R package helps extracting the acceptes species names and taxon IDs for a given vector of user provided species names. The function also extracts a  record of the kingdom (in column `kingdom`) to avoid misinterpretation of taxonomic homonyms. It also keeps a record of the taxon rank (in column `taxonRank`) for filtering purposes for traits recorded at the family or genus level. This information can be used for trait inferrence of higher taxonomic resolution using hierarchical probabilistic matrix factorization (Shan et al 2012, Schrodt et al 2015).

*< towards globally unique identifiers for traits >*

More difficult than the taxonomic reference is the standardised reference to defined functional traits, due to a lack of URIs or APIs (see above). Eventually, the field  `measurementTypeID` should refer to globally unique identifiers for a well defined measurement methodology. However, many measurements that qualify as traits following the definition above are motivated by the particular research question and demand a specific measurement methodology. Some trait data are drawn from a wide literature body with different approaches of reporting for instance body lengths or ecological information. 
Therefore, if no published trait list is available that can be referrenced via globally unique URIs or DOIs, traitdatasets should be accompanied by a dataset-specific glossary of traits. This should at minimum provide a human readable trait name and a unique (alphanumeric) identifier as well as an unambiguous verbal definition, the accepted factor levels (for categorical data) and expected units (for numerical data). 

<!-- ### Exploratories 

A first list of traits was compiled in a community effort, online questionaire. Further traits are added as need arises. 
 
specifics of some important groups traits. 
- life-history traits
- Morphometric traits
- phenological traits
- ... 

Trait list is maintained by BExIS team and curators for taxonomic groups, as well as core synthesis team. --> 

## Extensions for additional data layers

*< measurement or fact >*

For data not obtained from own measurement, the field `reference` provides a precise reference to the source of data. This should quote the key, book, or  database for literature data. For museum specimens, this should report the name of the collection (potentially provide an URI). If expert knowledge, this should name the authority. If trait database, provide reference to the original publication, DOI or URL of the trait-database.

To record potential sources of noise or bias, the methods and procedures of fixation and preservation of the specimen (column `preparations`), method of measurement (`measurementMethod`), the person conducting the measurement (`measurementDeterminedBy`), the date at which the measurement was obtained (`measurementDeterminedDate`) are recorded. 

One issue of transparency of data is that the degree of taxonomic resolution at the time of observation of the specimen might be unclear. For instance, for literature data, the  data source might report trait values on the family or genus level, but the data author infers and reports the trait data at species level (e.g. if the entire genus reportedly shares the same trait value). Those cases are documented in the column `measurementResolution`

For some measured values, authors would report aggregate data of repeated measurements or pooled measurements, e.g. by weighing multiple individuals simultaneously and calculating an average. In these cases, recording the number of individuals (`individualCount`) along with a dispersion measure (e.g. variance or standard deviation, `dispersion`) or range of values (e.g. min and max of values observed in the field `measurementValueMin`, `measurementValueMax`) is adviced. The field `statisticalMethod` names the method for data aggregation (e.g. mean or median) or averaging as well as the variation or range.

*< observation context (occurence) >*

This category of columns contains further information about the individual specimen or occurence that has been observed and measured. 

As a high-level discrimination of the source of the measurement or fact, the column `basisOfRecord` takes an entry about the type of trait data recorded: Were they taken by own measurement (distinguish "LivingSpecimen", "PreservedSpecimen", "FossilSpecimen") or taken from literature ("literatureData"), from an existing trait database ("traitDatabase"), or is it expert knowledge ("expertKnowledge"). It is highly recommended to provide further detail about the source in the column `basisOfRecordDetails`. 

For both literature and measured data, trait values may be recorded for different sub-categories of individuals of a taxon to capture polymorphisms, for instance differentiated by sex or life stage. The template provides the fields `sex`, `lifeStage`, `age`, and `morphotype` for this distinction.

Seasonal variation of traits may be recored by assigning a date and time of sampling to the occurcence, using the fields `year`,	`month` and	`day`, depending on resolution. The field definitions of the Darwin Core Standard can be applied instead, to refer to a geological stratum, for instance. 
Sampling may be further specified using a unique identifier for the sampling event `eventID`	which references to an external dataset. The record of a `samplingProtocol` may capture bias in samling methods. 

To capture geographic variation of traits, a set of fields for georeferencing can put the observation into spatial and ecological context (`habitat`, 	`decimalLongitude`,	`decimalLatitude`, `elevation`,	`geodeticDatum`, `verbatimLocality`, `country`, `countryCode`). The field `locationID` may be used to reference the occurence to a dataset-specific or global identifier. This allows the trait data to double as observation data, e.g. for upload to the GBIF database. 

<!-- ## The Biodiversity Exploratories Extensions and template 

Data will be uploaded to BExIS using the template to join data to the trait dataset while keeping full data authority: author information and ownership, access right management, as provided by BExIS. 

If applicable, trait values can be assigned to regions, plot IDs or sampling events which will then allow users to combine trait data with abundance, other observational data or the management regime on the sampled plots.

Metadata:
Each traitdataset uploaded to BExIS and added to the traitdatabase will be accompanied with a metadata file containing additional information on data origin, method, authors and owners (in redundancy with primary data, see above) and possibly more detailed definition of the traits recorded. 
--> 

## Metadata 

Individual measurements and facts will likely already belong to a larger set of traits or a separate traitdatabase before they are added to a combined traitdatabase. To retain the rights of the original data contributor, the field `rightsHolder` states the person or organization who owns or manages the rights to the data; `bibliographicCitation` states a bibliographic reference which should be cited when the data is used; and `license` specifies under which terms and conditions the data can be used, re-used and/or published. 
This information always applies to one single fact or measurement, further information on the larger dataset which originall contained this entry can be stored in `datasetID`, `datasetName`,`authorLastname` and `authorFirstname`. These columns should hence give credit to the person who compiled the original dataset and signs responsible for the correct identification and reporting of the rights holder.


## Computational tools for producing compliant data

We provide an R package to assist producing data compliant with the trait data standard proposed above. The package is being developed as an open source project on GitHub (https://github.com/fdschneider/traitdataform).

There are two major use cases for the package:

- preparation of own trait datasets for upload into public data bases, and
- harmonizing trait datasets from different sources by moulding them into a unified format.

The key function of the package is `as.traitdata()` which moulds a species-trait-matrix or occurence table data into a measurement longtable format. It also maps maps column names into terms provided in the trait data standard. 

Scientific taxon names are matched automatically to the GBIF Backbone Taxonomy (taxonomic ontology server) by calling the function `standardize.taxonomy()`

The `standardize.traits()` function matches user provided trait names onto public trait ontologies or links it to an own table of trait definitions, i.e. a thesaurus of traits. The same function harmonizes trait values into target units and legit factor levels. 

The output of these functions can easily be merged using the `rbind()`. 

In principle, transferring and harmonizing traitdata using the package is as simple as:

```r
library("traitdataform")
traitdataset1 <- standardize(read.csv("path/to/data.csv"),
            thesaurus = as.thesaurus("http://url.of/thesaurus.csv"),
            taxa = "name_correct", units = "mm")
```

For a detailled description on how to use the package see the package vignette (). The package is under continuous open source development and invites participation in development, comments or bug reports via the Github Issue page (). 

(figure 2 process chart from original file to standardized output)

# Discussion

- With these tools, traitdata will be easier to harmonize 

- decentralised structures, not limited by infrastructural projects

- open source community development, invite contributions to traitdata standard and toolchain of R-package

- encourage development of trait definitions and semantic ontologies

- a global analysis of ecological traits will be facilitated 


## Facilitate data availability & Synthesis mainstreaming

Make data assembly and usage of traits widely accessible. 

Enable addressing new synthesis questions on specific taxa and across taxa

for members of the Exploratories and outside of the Exploratories

Trait-data may serve as a pilot case for data standardisation for particular types of data assessed within the exploratories. This might be transferable to other data types, as well. 

potential to expand the framework across research projects. 

## Synthesis perspectives

Comparability of traits across taxa

Gap analysis

specificity of BE trait-data is local context of exploratories, if trait data are assessed on the site, trait variation can be related to land-use intensity. In this spatial extend this would be a novelty.

# Acknowledgements


# Authors' contributions


# References 

Allan, E., Manning, P., Alt, F., Binkenstein, J., Blaser, S., Bluthgen, N., Bohm, S., Grassein, F., Holzel, N., Klaus, V.H.,
Kleinebecker, T., Morris, E.K., Oelmann, Y., Prati, D., Renner, S.C., Rillig, M.C., Schaefer, M., Schloter, M., Schmitt, B.,
Schoning, I., Schrumpf, M., Solly, E., Sorkau, E., Steckel, J., Steffen-Dewenter, I., Stempfhuber, B., Tschapka, M.,
Weiner, C.N., Weisser, W.W., Werner, M., Westphal, C., Wilcke, W., Fischer, M., 2015. Land use intensification alters
ecosystem multifunctionality via loss of biodiversity and changes to functional composition. Ecol Lett. doi:
10.1111/ele.12469

Aubin, I., Venier, L., Pearce, J., Moretti, M., 2013. Can a trait-based multi-taxa approach improve our assessment of
forest management impact on biodiversity? 22, 2957-2975. doi: 10.1007/s10531-013-0565-6

Birkhofer, K., Diekötter, T., Meub, C., Stötzel, K., Wolters, V., 2015. Optimizing arthropod predator conservation in
permanent grasslands by considering diversity components beyond species richness. 211, 65-72. doi: 10.1016/j.agee.2015.05.014

Birkhofer, K., Smith, H.G., Weisser, W.W., Wolters, V., Gossner, M.M., 2015. Land-use effects on the functional
distinctness of arthropod communities. Ecography 38, 889-900. doi: 10.1111/ecog.01141

Börschig, C., Klein, A.M., von Wehrden, H., Krauss, J., 2013. Traits of butterfly communities change from specialist
to generalist characteristics with increasing land-use intensity. Basic Appl Ecol 14, 547-554. doi: 10.1016/j.baae.2013.09.002

Cadotte, M.W., Carscadden, K., Mirotchnick, N., 2011. Beyond species: functional diversity and the maintenance of
ecological processes and services. J. Appl. Ecol. 48, 1079-1087. doi: 10.1111/j.1365-2664.2011.02048.x

Chisté, M.N., Mody, K., Gossner, M.M., Simons, N.K., Köhler, G., Weisser, W.W., Blüthgen, N., 2016. Losers, winners,
and opportunists: How grassland land-use intensity affects orthopteran communities. 7, e01545. doi: 10.1002/ecs2.1545

de Bello, F., Lavorel, S., Albert, C.H., Thuiller, W., Grigulis, K., Dolezal, J., Janecek, S., Leps, J., 2011. Quantifying the
relevance of intraspecific trait variability for functional diversity. Methods Ecol. Evol. 2, 163-174. doi: 10.1111/j.2041-210X.2010.00071.x

Díaz, S., Purvis, A., Cornelissen, J.H.C., Mace, G.M., Donoghue, M.J., Ewers, R.M., Jordano, P., Pearse, W.D., 2013.
Functional traits, the phylogeny of function, and ecosystem service vulnerability. Ecology and evolution 3,
2958-2975. doi: 10.1002/ece3.601

Duarte, L.D.S., Carlucci, M.B., Fontana, C.S., Hartz, S.M., Pillar, V.D., 2011. Plant diaspore traits as indicators of
mutualistic interactions in woody vegetation patches developing into a grassland-forest mosaic. Community Ecol
12, 126-134. doi: 10.1556/ComEc.12.2011.1.15

Entling, W., Schmidt, M.H., Bacher, S., Brandl, R., Nentwig, W., 2007. Niche properties of Central European spiders:
shading, moisture and the evolution of the habitat niche. Global Ecol Biogeogr 16, 440-448. doi: 10.1111/j.1466-8238.2006.00305.x

Fontaine, C., Dajoz, I., Meriguet, J., Loreau, M., 2006. Functional diversity of plant-pollinator interaction webs
enhances the persistence of plant communities. PLoS biology 4, e1. doi: 10.1371/journal.pbio.0040001.g004

Forister, M.L., Novotny, V., Panorska, A.K., Baje, L., Basset, Y., Butterill, P.T., Cizek, L., Coley, P.D., Dem, F., Diniz, I.R.,
Drozd, P., Fox, M., Glassmire, A.E., Hazen, R., Hrcek, J., Jahner, J.P., Kaman, O., Kozubowski, T.J., Kursar, T.A., Lewis,
O.T., Lill, J., Marquis, R.J., Miller, S.E., Morais, H.C., Murakami, M., Nickel, H., Pardikes, N.A., Ricklefs, R.E., Singer,
M.S., Smilanich, A.M., Stireman, J.O., Villamarin-Cortez, S., Vodka, S., Volf, M., Wagner, D.L., Walla, T., Weiblen,
G.D., Dyer, L.A., 2015. The global distribution of diet breadth in insect herbivores. Proceedings of the National
Academy of Sciences of the United States of America 112, 442-447. doi: 10.1073/pnas.1423042112

Gamez-Virues, S., Perovic, D.J., Gossner, M.M., Borschig, C., Bluthgen, N., de Jong, H., Simons, N.K., Klein, A.M.,
Krauss, J., Maier, G., Scherber, C., Steckel, J., Rothenwohrer, C., Steffan-Dewenter, I., Weiner, C.N., Weisser, W.,
Werner, M., Tscharntke, T., Westphal, C., 2015. Landscape simplification filters species traits and drives biotic
homogenization. 6, 8568. doi: 10.1038/ncomms9568

Garnier, E., Laurent, G., Bellmann, A., Debain, S., Berthelier, P., Ducout, B., Roumet, C., Navas, M.L., 2001.
Consistency of species ranking based on functional leaf traits. 152, 69-83. doi: 10.1046/j.0028-646x.2001.00239.x

Gossner, M.M., Lewinsohn, T.M., Kahl, T., Grassein, F., Boch, S., Prati, D., Birkhofer, K., Renner, S.C., Sikorski, J.,
Wubet, T., Arndt, H., Baumgartner, V., Blaser, S., Bluthgen, N., Borschig, C., Buscot, F., Diekotter, T., Jorge, L.R.,
Jung, K., Keyel, A.C., Klein, A.M., Klemmer, S., Krauss, J., Lange, M., Muller, J., Overmann, J., Pasalic, E., Penone, C.,
Perovic, D.J., Purschke, O., Schall, P., Socher, S.A., Sonnemann, I., Tschapka, M., Tscharntke, T., Turke, M., Venter,
P.C., Weiner, C.N., Werner, M., Wolters, V., Wurst, S., Westphal, C., Fischer, M., Weisser, W.W., Allan, E., 2016.
Land-use intensification causes multitrophic homogenization of grassland communities. 540, 266-269. doi:
10.1038/nature20575

Gossner, M.M., Simons, N.K., Achtziger, R., Blick, T., Dorow, W.H.O., Dziock, F., Köhler, F., Rabitsch, W., Weisser,
W.W., 2015. A summary of eight traits of Coleoptera, Hemiptera, Orthoptera and Araneae, occurring in grasslands
in Germany. Scientific Data 2, 150013. doi: 10.1038/sdata.2015.13

Gossner, M.M., Simons, N.K., Höck, L., Weisser, W.W., 2015. Morphometric measures of Heteroptera sampled in
grasslands across three regions of Germany. 96, 1154. doi: 10.1890/14-2159.1

Hopfenmuller, S., Steffan-Dewenter, I., Holzschuh, A., 2014. Trait-specific responses of wild bee communities to
landscape composition, configuration and local factors. PloS one 9, e104439. doi: 10.1371/journal.pone.0104439

Jennings, N., Pocock, M.J.O., 2009. Relationships between Sensitivity to Agricultural Intensification and Ecological
Traits of Insectivorous Mammals and Arthropods. 23, 1195-1203. doi: 10.1111/j.1523-1739.2009.01208.x

Kühsel, S., Blüthgen, N., 2015. High diversity stabilizes the thermal resilience of pollinator communities in
intensively managed grasslands. 6, 7989. doi: 10.1038/ncomms8989

Kühsel, S., Brückner, A., Schmelzle, S., Heethoff, M., Blüthgen, N., 2016. Surface area-volume ratios in insects. doi:
10.1111/1744-7917.12362

Lavorel, S., Garnier, E., 2002. Predicting changes in community composition and ecosystem functioning from plant
traits: revisiting the Holy Grail. 16, 545-556. doi: 10.1046/j.1365-2435.2002.00664.x

Menezes, S., Baird, D.J., Soares, A.M.V.M., 2010. Beyond taxonomy: a review of macroinvertebrate trait-based
community descriptors as tools for freshwater biomonitoring. 47, 711-719. doi: 10.1111/j.1365-2664.2010.01819.x

Moretti, M., de Bello, F., Ibanez, S., Fontana, S., Pezzatti, G.B., Dziock, F., Rixen, C., Lavorel, S., 2013. Linking traits
between plants and invertebrate herbivores to track functional effects of land-use changes. J Veg Sci 24, 949-962.
doi: 10.1111/jvs.12022

Renner, S.C., Gossner, M.M., Kahl, T., Kalko, E.K., Weisser, W.W., Fischer, M., Allan, E., 2014. Temporal changes in
randomness of bird communities across Central Europe. Plos One 9, e112347. doi: 10.1371/journal.pone.0112347

Simons, N.K., Gossner, M.M., Lewinsohn, T.M., Boch, S., Lange, M., Muller, J., Pasalic, E., Socher, S.A., Turke, M.,
Fischer, M., Weisser, W.W., 2014. Resource-mediated indirect effects of grassland management on arthropod
diversity. PLoS One 9, e107033. doi: 10.1371/journal.pone.0107033

Simons, N.K., Weisser, W.W., Gossner, M.M., 2016. Multi-taxa approach shows consistent shifts in arthropod functional traits along grassland land-use intensity gradient. Ecology 97, 754-764. doi: 10.1890/15-0616.1

Violle, C., Navas, M.-L., Vile, D., Kazakou, E., Fortunel, C., Hummel, I., Garnier, E., 2007. Let the concept of trait be
functional! 116, 882-892. doi: 10.1111/j.0030-1299.2007.15559.x

Weiner, C.N., Werner, M., Linsenmair, K.E., Bluthgen, N., 2014. Land-use impacts on plant-pollinator networks:
interaction strength and specialization predict pollinator declines. Ecology 95, 466-474.

Weiner, C.N., Werner, M., Linsenmair, K.E., Blüthgen, N., 2011. Land use intensity in grasslands: Changes in
biodiversity, species composition and specialisation in flower visitor networks. 12, 292-299. doi: 10.1016
j.baae.2010.08.006

---
output:
  pdf_document: default
  html_document: default
---

# A trait-data framework for the Biodiversity Exploratories

## Introduction

### The concept of functional traits in biodiversity research

Functional traits are phenotypic characteristics that are related to the fitness and performance of an organism. 

Traits can be measurements of morphology of animals or plants, life-history traits such as reproductive strategies, physiological traits including metabolism and photosynthetic activity, feeding traits, biochemical and isotopic compounds, as well as environmental traits. 

Source of trait data can be direct measurements, literature values, expert knowledge. 
Some studies propose a differentiation of effect traits and response traits (or  performace and fitness traits), which may be depending on the research question. 

Given this range of measures, traits are assessed with multiple questions in mind. 

at individual scale: evolution of adaptive traits, intraspecific variation, at species scale: Morphology and phylogeny, ecological function and trophic role, biotic interactions. 
at ecosystem scale: functional composition of communities, community weighted means and variance, ecosystem service provisioning. 
at global spatial and temporal scale: global spectrum of form and function, biogeography, palaeoecology

A focus on functional traits allows to describe the role of a species in an ecosystem or its ability to persist under certain environmental conditions. 

Traits help in bridging individual level behaviour and physiology into processes at the ecosystem scale.

traits help to identify economic strategies of organisms, beyond taxonomy

Refer to Katke et al 2011, Violle et al 2007, Diaz et al 2007, McGill et al., 2006, ...

### trait-based research within the exploratories

Refer to successfully published papers on arthropod traits, multi-trophic trait variation etc. 

Allen et al 2015
Boerschig et al 2013
Gossner et al 2015 & 2016
Simons et al 2014 & 2016
Kühsel et al 2015 & 2016

Summarize different questions, currently proposed in above- and below ground work within the Exploratories, focus on plant traits, arthropod traits, microbial traits.

Need to unify for multi-trophic integration

Trait matching integrates function across trophic levels, influence of land use and environmental filtering on trait composition, Exploratories are ideal framework for testing

## Common structure of trait datasets

Traitdata have been standardised into databases. e.g. plant traits have a head start and were drawn from different ressources into the TRY database. For animals, a variety of traitdata bases exist. 

(table of existing databases?)

All databases come with their own structure, which reflects the research questions of the research initiatives and their organismal focus. 

### minimal definition of traid-datasets 

As a minimum consensus, trait datasets may be defined as follows: 
A trait-dataset contains measurements or facts (i.e. measurement values) about phenotypic characteristics of fitness or performance (i.e. measurement types, or traits) assigned to an entity of a biological taxon (i.e. an observation of a species or higher taxon). The entity or observation to which the reported measurement or fact apllies may differ in resolution -- depending on the scientific question -- and could be a subsample or bodypart, an individual specimen, an entire species or higher-level taxon. 

### standardised reference to taxon and trait definitions 

To obtain digitized datasets being comparable, much effort has gone into the development of precise definitions and standardised reference lists of taxon names and trait definitions.

Relevant for all domains of biodiversity data, authors and data managers must provide compatibility to other datasets by referencing their data to published taxonomic ontologies, which exist for all organism groups and many regions of the world (examples!). Widest coverage today may be found in the GBIF backbone taxonomy or ... . This may be acheived by referencing an observation to a unique identifier (which can be either alpha-numeric or full taxon name, including author and date of first description, or a unambiguous Unique Resource Identifier, URI, which refers to a precisely defined term in a published ontology) and provide the information to which ontology the taxon names refer to in the metadata.

Similarly motivated, traits for target organism groups and ecosystems have been categorized and defined in thesauri  (e.g., Plant Trait Ontology [20] or Vertebrate Trait Ontology [28]) or ontologies (morphometrics?), which also provide unique identifiers for referencing along with more or less precise definitions of the body measures, morphometric landmarks, categorical traits or environmental conditions, for instance. Ideally, these thesauri also define a target measurement unit or constrain factor levels. Multiple approaches have spawned around the initialisation of trait databases, most advanced certainly for plant traits in the TRY database and its reference Thesaurus of Plant characteristics (TOP).  

Traits must not only be defined in terms of their interpretation, but ideally also be standardised in terms of numerical units and, evene more important, the use of factor levels. This is challenging given the range of data types that fall within datasets of functional traits: numerical values represent measurements of length, volumes, ratios, rates or timespans. integer values may apply to count data (e.g. eggs per clutch). binary data (encoded as 0 or 1) or logical data (coded as TRUE or FALSE) may apply to qualitative traits such as ... . Many traits are categorical and allow for a constrained set of factor levels, such as ... () or unconstrained entries such as color. Some traits take character strings of descriptions. Finally there are specific formats of multivariate trait values (e.g. x.y.z coordinates of a landmark measured in 3D space or relative abundance of chain-lengths in biochemical compounds).
To achieve comparability of traits across taxonomic groups, some trait standards suggest a hierarchical classification or a relational tree of functional traits (e.g. TOP or T-SITA). This links traits of similar meaning and allow cross-taxon comparative studies.  
Thus, a trait thesaurus should assign trait names with A) a unique definition and B) an expected format of measured values or reported facts, and might additionally provide C) a hierarchical or tree-based classification of traits. 

We found that few trait standards have developed online-ready implementations of their ontologies, i.e. provide a static URI or even an API to refer to or extract definitions. It remains an important task for biodiversity data management initiatives to provide these.  

### traitdata formats 

Such trait-datasets take different formats. For instance, if trait data have been collated at the species level from different literature sources or from expert knowledge, they usually are reported in a species \times trait matrix format, with a column of trait values for each trait recorded and a row for each species (or taxon) for which data were available. This format is usually reporting missing data as NA. It may store additional information (e.g. on variation of means or literature source) in secondary colums. The matrix format is widely used for the production of lookup-tables at the species level, which for instance may be used for the calculation of community weighted means or functional diversity metrics at the community level (Refs). Also, missing information about the behaviour and functional role of species of little ecological record may be inferred from these tables (Refs).  

For investigations of within species variation of traits, traits would be recorded per observation, i.e. each individual specimen would be recorded in a row, with the traits measured on it stored in columns. Those data are common in investigations of evolutionary trade-offs and trait correlation, or of intra-specific variation and sexual dimorphism.   

Computationally most effective and allowing for highest flexibility is the storage of traitdata in long-table formats, where each row is reserved for a single measurement or fact, referenced to a single observation (i.e. a specimen or taxon) and a trait definition. This allows for repeated measurements, even on a single individual. Also, multivariate trait measurements can be recorded in this format by linking multiple rows via a unique measurement ID. 
The latter format is therefore providing the highest resolution and ideal for storing raw data of trait measurements in huge databases and link them via the respective unique identifiers to additional information, such as location or taxonomy.  

### additional information on trait records

<!-- additional information -->
In addition to the minimal definition above, trait-datasets may come with a variety of additional information. The long-table format is ideal for storing this metadata-information on the measurement level. The matrix or table format would have to keep this information referenced in metadata or linked datasets. 

(We conceptualize trait-datasets to  not include information about a species' interaction partners/associations of an organism, since they are -- to our understanding -- not within the scope of functional traits. However, such network data may be of interest to be combined with trait data. )


basisofRecord: 

### additional detail on measurement or fact

Data resolution differs and researchers might report aggregated species averages or replicates of individual measurements. A universally applicable framework needs to fall back to the smallest unit, i,e. the single measurement (Kattge  et al 2011), and allow multiple measurements of a single trait for a single species at a single site (i.e. one observation). Indeed this resolution is necessary for assessing intra-specific trait variation, or even variation of traits of a single specimen (e.g. size of leaves of a single tree).  In case of aggregated measurements, however, researchers might record the average and the dispersal, and also keep information about the statistical method of a average record and the dispersal metric (e.g. variance or range) as well as the number of individuals aggregated. Having this information available, would allow compiling weighted averages of species traits by combining data of  different resolution.
measurementID

In the case of measured data, the method and accuracy of measurement, the methods of sampling or preservation of the specimen, as well as the person measuring, would be recorded to assess any methodological bias.
The measurements most likely were taken under certain natural or artificial environmental conditions, that might also be recorded along with the trait data. A protocoll of measurement might be referred to. 

In case of datasets collating information from other sources, literature would be referenced or an expert name reported. For museum specimens or private collections, the unique identifier of the museum collection would link the measurement to a real physical object.

(Many of the information described in the previous two section are defined in the [Darwin Core Extension Measurement or Fact](). )

#### additional information on observation context /occurence level information

The entity at which the measurement was obtained or to which it refers to may be further detailled: Some traits are recorded as species or population level averages, such as functional guild assignment or average longevity. In that case, the taxon rank to which the measurement applies needs to be documented. 
Similarly, measurements might resolve to lower than species level, to subspecies, or even sub-groups of a single species, like a sex, caste, or morphotype. 

specimenID  / occurenceID

Trait data may be recorded from specimens which developed in a particular spatial and climatic context, or cultivated under (semi-)controlled conditions. A dataset should report these details.  

Therefore, georeference, altitude and date of sampling would be recorded to capture and investigate climate and location as a source of trait variation. A unique location identifier may link the observation to an experimental context or dataset-specific reference table or a global database of locations. To add ecological context, the habitat type where the specimen was observed could be classified.


(Most of the information described in the last two sections are subsumized under the [Occurence Extension of the Darwin Core](http://tools.gbif.org/dwca-validator/extension.do?id=http://rs.tdwg.org/dwc/terms/Occurrence#Occurrence), and may also be referenced into an external database via a unique Occurence identifier. ) 

### information on attribution and permissions to use

Finally, an own class of information might apply to the entire trait-dataset, which classifies them as metadata. Since trait data are of great use for synthesis studies, information about how the data may be distributed, re-used and attributed to are of particular importance for  trait datasets. Most researchers encourage re-use of their published datasets while making sure they are sufficiently credited. The use of permissive licenses for traitdata publications, such as Creative Commons Attribution 4.0 or Public Domain release, has been established as the gold standard. 

<!-- Where is this data record available online? Source in the Measurements or Facts extension file is for a url to be displayed alongside the data point, so EOL visitors can click through to an online resource where the data originated. This might be a dataset stored at an online repository, a taxon page on a website, or any other online location.
What shall I cite if I use this data record in a publication? BibliographicCitation in the Measurements or Facts extension file is for the suggested citation format for a user of this dataset to include in a references list or bibliography. Even if the data record or dataset have never been published elsewhere, we recommend that you craft an appropriate citation so others can provide proper credit.
If the dataset is from a literature review, and one or more references are available for individual data points, these references should be recorded in the References extension and listed by their Reference IDs in the ReferenceID field of the Measurements or Facts extension file, see below.  -->

## Towards a traitdata standard 

In this paper, we propose a universal scheme of defined column names and data structure that captures the different degrees of resolution and measurement detail for multiple use cases of trait data. 

Existing initiatives for standardising data are focused on a constrained organism group, ecosystem type or region and compile data in own centralised databases. Among the different  approaches, the TRY database for plant characteristics is certainly the one with highest coverage. The most inclusive trait database to date has been created in the framework of the Encyclopedia of Life (EOL) with TraitBank (Parr et al 2015). With the framework presented here, we aim for compatibility with those standards.

However, while TraitBank and TRY are centralised infrastructures, we want to facilitate the use of a standard format of trait data by suggessting a  flexible formatting scheme that can be applied in multiple contexts (e.g. in context of a taxon-specific database; in user-side compilations of trait data from different sources). 

For standardisation and comparability of traitdata across datasets, conventions on trait definitions and taxon names are inevitable. We consider the fact that authors have their own local schemes for standardisation and may contribute to different communities. 
_user/_orig substring: 

The trait-dataset may be linked to supporting information (e.g. on the occurence, the methodology, the original source, the sampling event or location) on the metadata level or in attached data tables, e.g. in the form of a Darwin Core Archive, or into external databases via URIs. For this interlinkage with other datasets, columns are reserved for unique identifiers (e.g. linking measurements to location, collections, literature) that refer to a dataset specific or globally defined ID. 

In the subsequent sections we propose columns that compose a traitdataset, starting with the ones required for our minimal definition of trait-datasets proposed above and continueing with columns that add information on the level of the occurence, the measurement or fact, and the entire record.  


#### core columns 

For the minimal definition of trait-datasets, the key identifier columns are the ones referencing an accepted taxon name (`scientificName` & `taxonID`) as well as a defined trait name (`measurementType`, `traitID`). The key content of a row is the observed measurement or fact, which is composed of a value (`measurementValue`) and -- for numeric values -- a standard unit (`measurementUnit`). To ensure compatibility at the side of the data provider and for quality checking the data table ought to keep the original names and values as used by the data provider in columns appending the suffix `_original` (i.e. `scientificName`, `measurementType`, `measurementValue`, `measurementUnit`). 

Each measurement should be labelled by a unique identifier (i.e. each row of the dataset, except for multivariate traitdata; see below). 
To ensure compatibility of datasets of different origin, we propose to use a cryptographic hash function for the generation of a globally unique identifier of each measurement (`measurementID`). Cryptographic hash functions compile strings of variable content length into a bit string of fixed size. This string can be used to compare data and check for duplicates across multiple datasets. The method we propose is to collate a string of all original data columns `_original` and parse them using the SHA1 algorithm. 

we provide code and assistance in the R package described below. 

Compatibility issues: 

Challenges and subspecies
Use beyond trait analyses

Taxonomic level resolution: some traits will be assessed on family or genus level. This information can be later used for trait prediction of higher taxonomic resolution using hierarchical probabilistic matrix factorization (Shan et al 2012, Schrodt et al 2015).  


### A standard list of species traits

Trait data are mostly defined by the research question. Some trait data are easily available from literature, some have been measured by the authors. 

A first list of traits was compiled in a community effort, online questionaire. Further traits are added as need arises. 
 
specifics of some important groups traits. 
- life-history traits
- Morphometric traits
- phenological traits
- ... 

factorial vs. numerical traits, standardise factor levels and range of data. Keep record of trait data variation (min and max) to warn about implausible datasets. 

Trait list is maintained by BExIS team and curators for taxonomic groups, as well as core synthesis team. 

### The template 

Data will be uploaded to bexis using the template to join data to the trait dataset while keeping full data authority: author information and ownership, access right management, as provided by BExIS. 

Primary data: one column per measurement, refering to a valid species ID and a valid trait ID (mandatory). 

Columns contain information on ownership and origin of data, which is redundant with Metadata, but necessary to transfer these information into merged datasets. 

Optional:
capture intra-specific variation by measuring replicates, recording mean and variation, ranges
sex-related trait variation, male-female dimorphisms
Morphotypes: in eusocial insects,
age related trait variation: growth dependency, life stages, polymorphism, 

if applicable, trait values can be assigned to plot IDs or regions. 

compatibility with other trait databases: columns that are mandatory in TRY: ... 

Metadata:
contain additional information on data origin, method, authors and owners (in redundancy with primary data, see above) and possibly more detailled definition of the traits recorded. 

### A tool for producing compliant data

R Script for matching species names and trait IDs; automated filling of metadata columns (author name, etc). 

Bexis quality upload check; assignment of BExIS ID. 

### Tools for using data

BExIS ownership and access control; query form for downloading data. 

R Script to download, filter and merge data  

## Added benefit

### Facility data availability & Synthesis mainstreaming

Make data assembly and usage of traits widely accessible for members of the Exploratories and outside of the Exploratories

Enable addressing new synthesis questions on specific taxa and across taxa

Trait-data may serve as a pilot case for data standardisation for particular types of data assessed within the exploratories. This might be transferable to other data types, as well. 

potential to expand the framework across research projects. 

### Synthesis perspectives

Comparability of traits across taxa

Gap analysis

specificity of BE trait-data is local context of exploratories, if trait data are assessed on the site, trait variation can be related to land-use intensity. In this spatial extend this would be a novelty.

## Possibility for participation

contribute data 
- trait lists & replicated measurements
- species lists

(When uploading trait data, consider opting for open data)

join discussion on trait-data requirements, comment on template 

report issues with R tool, file pull-requests on GitHub, Maintainer of R package: Florian Schneider



# References 

Gámez-Virués S., Perović D. J., Gossner M. M., Börschig C., Blüthgen N., de Jong H., Simons N., Klein A.-M., Krauss J., Maier G., Scherber C., Steckel J., Rothenwöhrer C., Steffan-Dewenter I., Weiner C. N., Weisser W. W., Werner M., Tscharntke T., Westphal C. (2014): Landscape simplification filters species traits and drives biotic homogenization. Nature Communications 6: 8568. doi: 10.1038/ncomms9568  
Gossner M. M., Simons N. K., Achtziger R., Blick T., Dorow W. H. O., Dziock F., Köhler F., Weisser W. W. (2015): A summary of eight traits of Coleoptera, Hemiptera, Orthoptera and Araneae, occurring in grasslands in Germany. Scientific Data 2:150013. doi: 10.1038/sdata.2015.13  
Gossner M. M., Simons N. K., Höck L., Weisser W. W. (2015): Morphometric measures of Heteroptera sampled in grasslands across three regions of Germany. Ecology 96 (4), 1154–1154. doi: 10.1890/14-2159.1   
Gossner, M. M., Lewinsohn, T. M., Kahl, T., Grassein, F., Boch, S., Prati, D., ... & Allan, E. (2016). Land-use intensification causes multitrophic homogenization of grassland communities. Nature, 540(7632), 266-269.  
Simons N. K., Weisser W. W., Gossner M. M. (2016): Multi-taxa approach shows consistent shifts in arthropod functional traits along grassland land-use intensity gradient. Ecology 97 (3), 754–764. doi: 10.1890/15-0616.1   
Simons N. K., Gossner M. M., Lewinsohn T. M., Boch S., Lange M., Müller J., Pasalic E., Socher S. A., Türke M., Fischer M., Weisser W. W. (2014): Resource-Mediated Indirect Effects of Grassland Management on Arthropod Diversity. PLoS ONE 9 (9): e107033. doi:10.1371/journal.pone.0107033   
Chisté, M. N., Mody, K., Gossner, M. M., Simons, N. K., Köhler, G., Weisser, W. W., & Blüthgen, N. (2016). Losers, winners, and opportunists: How grassland land‐use intensity affects orthopteran communities. Ecosphere, 7(11).  
Birkhofer K., Smith H. G., Weisser W. W., Wolters V., Gossner M. M. (2015): Land-use effects on the functional distinctness of arthropod communities. Ecography 38 (9), 889–900. doi: 10.1111/ecog.01141   
Birkhofer K., Diekötter T., Meub C., Stötzel K., Wolters V. (2015): Optimizing arthropod predator conservation in permanent grasslands by considering diversity components beyond species richness. Agriculture, Ecosystem and Environments 211, 65–72. doi: 10.1016/j.agee.2015.05.014   
Weiner C. N., Werner M., Linsenmair K. E., Blüthgen N. (2014): Land-use impacts on plant–pollinator networks: interaction strength and specialization predict pollinator declines. Ecology 95 (2), 466–474. doi: 10.1890/13-0436.1  
Börschig, C., Klein, A. M., von Wehrden, H., & Krauss, J. (2013). Traits of butterfly communities change from specialist to generalist characteristics with increasing land-use intensity. Basic and Applied Ecology, 14(7), 547-554.  
Kühsel S., Blüthgen N. (2015): High diversity stabilizes the thermal resilience of pollinator communities in intensively managed grasslands. Nature Communications 6:7989. doi: 10.1038/ncomms8989   
Kühsel S., Brückner A. K., Schmelzle S., Heethoff M., Blüthgen N. (2016): Surface area–volume ratios in insects. Insect Science, in press. doi: 10.1111/1744-7917.12362   
Renner S. C., Gossner M. M., Fischer M., Kahl T., Kalko E. K. V., Weisser W. W., Allan E. (2014): Temporal changes in randomness of bird communities. PLoS ONE 9(11): e112347. doi:10.1371/journal.pone.0112347   
Allan E., Manning P., Alt F., Binkenstein J., Blaser S., Blüthgen N., Böhm S., Grassein F.,  Hölzel N., Klaus V., Kleinebecker T., Morris K. E., Oelmann Y., Prati D., Renner S. C., Rillig M. C., Schäfer M., Schloter M., Schmitt B., Schöning I., Schrumpf M., Solly E., Sorkau E., Steckel J., Steffen-Dewenter I., Stempfhuber B., Tschapka M., Weiner C. N., Weisser W. W., Werner M., Westphal C., Wilcke W., Fischer M. (2015): Land use intensification alters ecosystem multifunctionality via loss of biodiversity and changes to functional composition. Ecology Letters 18 (8), 834–843. doi: 10.1111/ele.12469  


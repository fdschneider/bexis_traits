
# A trait-data framework for the Biodiversity Exploratories

## Introduction

### The concept of functional traits in biodiversity research

Functional traits are phenotypic characteristics that are related to the fitness and performance of an organism. 

Traits can be measurements of morphology of animals or plants, life-history traits such as reproductive strategies, physiological traits including metabolism and photosynthetic activity, feeding traits, biochemical and isotopic compounds, as well as environmental traits. 

Source of trait data: measurements, literature values, expert knowledge. 

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

## Unifying trait data

Traitdata have been standardised into databases. e.g. plant traits have a head start and were drawn from different ressources into the TRY database. For animals, a variety of traitdata bases exist. 

All databases come with their own strucutre, which reflects the research questions of the initiatives and organismal focus. 
In sum, a variety of information may be stored along with trait data: 

In the case of measured data, the method of measurement and methods of sampling or preservation of the specimen, as well as the person measuring, would be recorded to assess any methodological bias. In case of data from other sources, literature would be referenced or an expert name reported. For museum specimens, the unique identifier of the museum collection would link the measurement to a real physical object. 

Data resolution differs and researchers might report aggregated species averages or replicates of individual measurements. A universally applicable framework needs to fall back to the smallest unit, i,e. the single measurement (Kattge  et al 2011), and allow multiple measurements of a single trait for a single species at a single site (i.e. one observation). Indeed this resolution is necessary for assessing intra-specific trait variation, or even variation of traits of a single specimen (e.g. size of leaves of a single tree).  In case of aggregated measurements, however, researchers might record the average and the dispersal, and also keep information about the statistical method of a average record and the dispersal metric (e.g. variance or range) as well as the number of individuals aggregated. Having this information available, would allow compiling weighted averages of species traits by combining data of  different resolution.

Some traits are recorded as species or population level averages, such as functional guild assignment or average longevity. In that case, the taxon rank to which the measurement applies needs to be documented. 
Similarly, measurements might resolve to lower than species level, to subspecies, or even sub-groups of a single species, like a sex, cast, or morphotype. 

Trait data may be recorded from specimens which developed in a particular spatial and climatic context. The measurement will be taken under certain natural or artificial environmental conditions, that might also be recorded along with the trait data. 

This also exemplifies the range of data types that fall within datasets of functional traits: numerical values represent measurements of length, volumes, ratios, rates or timespans. integer values may apply to count data (e.g. eggs per clutch). binary data (encoded as 0 or 1) or logical data (coded as TRUE or FALSE) may apply to qualitative traits such as ... . Many traits are categorical and allow for a constrained set of factor levels, such as ... () or unconstrained entries such as color. Some traits take character strings of descriptions. Finally there are specific formats of multivariate trait values (e.g. x.y.z coordinates of a landmark measured in 3D space or relative abundance of chain-lengths in biochemical compounds).   

In this paper, we propose a universal scheme of defined column names that captures the different degrees of resolution and measurement detail. 

For standardisation and comparability of traitdata across datasets, conventions on trait definitions and taxon names are inevitable. We consider the fact that authors have their own local schemes for standardisation and may contribute to different communities. 

_user substring: 



The traitdataset may be linked to supporting information on the metadata level or in external databases

ID columns: linking measurements to location, collections, literature



### taxonomic standardisation 

researchers need to refer each measurement  a standardised taxonomic terminology of species names. 

### A reference list of species names 

Importance of a unified species list

Compatibility issues: 

Challenges and subspecies

Use beyond trait analyses

Taxonomic level resolution: some traits will be assessed on family or genus level. This information can be later used for trait prediction of higher taxonomic resolution using hierarchical probabilistic matrix factorization (Shan et al 2012, Schrodt et al 2015).  

Maintainance of this list is with BExIS and a group of curators for different taxonomic groups.

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

### Tools for producing compliant data

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


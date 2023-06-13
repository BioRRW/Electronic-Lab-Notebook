## Aims-Overview
1. improved DISTILLATE and PRODUCT level capabilities and visualizations
2. integrating data from multiple biological modalities for refined annotation and profiling of community interactions
3. expanding DRAM interoperability and training to enrich the user experience


## Key Deliverable
*The key deliverable of this proposed project is a major release of DRAM, here considered version 2 (DRAM2), in October 2024, with releases scheduled for the duration of this project.*

## Detailed Aims
### Aim1:
- **Modularize DRAM annotations and visualizations to enable annotation customization, efficiency, and scalability.** A modular implementation of the DRAM algorithm provides users with customizable annotations for enhanced metabolic and ecosystem specificity and expert curation of traits with improved visualization. Outcomes from this aim will result in more precise annotations and updated visualizations, leading to readily available distillation of microbial traits and phenotypes from microbial genomic data.
- Deliverables for this aim include a revised trait app that incorporates carbon decomposition calls, along with new _ecosystem and topic toolkits_. Revised traits will not only enhance the user experience by enabling classification of MAGs into carbon use categories but will also be an integral part of predicting interactions in Aim 2 and model refinement in Aim 3. Additionally, our collaborations to build these toolkits will help us identify needed metabolisms and databases that should be incorporated into DRAM2. Lastly, it is our hope that standardizing the collection and reporting of ecosystem appropriate gene sets will facilitate more robust genomic analyses across laboratories and publications.

### Aim2:
- **Develop a multi-omics analysis toolkit for improved phenotypic and multi-organismal annotations.** We will build pathway representatives of ecosystem critical annotations and improve statistical analyses through the ingestion of gene expression and metabolite data. Using our existing pathway completion feature, DRAM will calculate the most active pathways and improve inferences on pathway directionality, both of which are features needed to accurately infer metabolic handoffs and niche overlap.
- Deliverables from this aim include 2 new toolkits (_ingest, multi-omics_) and a new build trait app within the _phenotype toolkit_. New visualizations include (i) figures of pathways painted with multi-omic data, (ii) output of statistically enriched/depleted genes and pathways, and (iii) correlation plots and relevance network plots. We not only provide automation of steps manually done by our laboratories but provide users with the means to interactively explore their data and visualizations that provide new perspectives on the interactions between organisms.

![[Pasted image 20230613133942.png]]

### Aim3:
- **Enhance DRAM interoperability with existing, broadly used, genomics-based software and cultivate our user community.** To make DRAM more interoperable with downstream applications we developed DRAM modes. These modes operate as pipelines which run customized analyses to generate automated outputs specific to their intended software targets. We will also offer training workshops to encourage user engagement, many of these in collaboration with the KBase team.
- Deliverables of Aim 3 include development of three modes of DRAM2 including DRAM2-genomemodel, DRAM2-traitmodel, and DRAM2-lite and their integration into four genome science platforms including KBase, BioCrunch, Aviary, and NMDC EDGE.  To promote DRAM2 and strengthen usability, we will host 3 workshops/year for the project period. Beyond advancement of this genomics tool, this interoperability along with new features of DRAM2 (Aims 1 and 2) will advance genome annotation as a whole through rapid integration of new biochemistry into genome annotation (workshops), iterative validation between models and annotations (BioCrunch, KBase models), and standardization of metagenomic workflows (NMDC EDGE, Aviary). In summary, DRAM2 outlined here will become one of the core tools for systems biology research based on our capacity to consolidate functional annotations in terms of biochemical pathways and extend these findings to organismal interactions, biogeochemical cycles, and predictive frameworks.

Figure from DOE grant: Schematic highlight of Aim 3
![[Pasted image 20230613134954.png]]

### Figure 3 from DOE grant

![[Pasted image 20230613132316.png]]
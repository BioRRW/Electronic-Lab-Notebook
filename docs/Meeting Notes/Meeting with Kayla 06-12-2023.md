---
title: Meeting with Kayla 06-12-2023
allDay: true
date: 2023-06-12
completed: null
---

Title: {{Meeting with Kayla} 
Date: {{2023-06-12}} 
Time: {{10:00}} 

Ongoing [[Projects]]/[[Grants]]:

[[DRAM]]
	OG DRAM - FUNDED
		Never really had its own funding
		Mike Schafer was the reason the pipeline became "DRAM"
			The Wrighton lab had a pipeline but Mike wanted to build it into a real pipeline
	[[DRAM-V]]
		Matt Sullivan at OSU
	DOE Comp Bio - Miller CU Denver - FUNDED
		**This is the grant that I am on and payed from**
		This grant is for improving annotations beyond homology
		The idea is to incorporate what they are doing into DRAM/DRAM2
		This also includes DRAM on KBASE: involves upkeep and such
	DOE Comp Bio - submitted grant - Will find out in the Fall
		**AIMS**
			1. modularize DRAM
				1. divide into little "Apps"
			2. New Features
				1. visualization/web dev. - this would involve hiring a web dev person
			3. Integration with other platforms
				1. problem b/c databases are huge
				2. maybe create a DRAM "light"
					1. still to be used on a server
					2. This will need to go on the Microbiome CSU Group new server
						1. TUNE Grant from CSU
						2. DRAM "light" will go on this
					3. Modeling
						1. BioCrunch - LBNL
						2. EcoSys - Ecosystems scale model - can ingest microbial data
						3. Both 1. and 2. are relavent to EMERGE and Wetlands. We have money to get DRAM to make automated outputs and needs to be made friendly to make required output formats into 1. and 2.

Other stuff related to DRAM
	[[EMERGE]]/PermaFrost/Lakes
		All permafrost grants
		All have DRAM written into them in some way or form (mostly w.r.t. modeling)
			i.e. genome function into models
		EMERGE -OSU [[Matt Sullivan]]
		Permafrost - DOD - NEW
		Lakes - lakes that surround permafrost
		[[Wetlands]] - Wrighton-led project
			

[[DRAM and DRAM2]]
	Kayla is sending latest (un-submitted) grant draft
	This will be good to review to see what they want and what they said they would do
	I need to read this


Other projects - will prob. not work on
	[[NIH - Salmonella]] - Ikia's stuff - money is gone - writing new grants
		Maybe some short analyses for proof-of-concept stuff
	[[NIH-Methylamines]] - grant being written
	

In short...
	All of these things depend on DRAM
		have Kegg and other annotation databases
	Some people are making other databases (i.e. related to shale fraking) which are packaged 
		These are really helpful for publishing and for data re-use and sharing
	We want to have DRAM light and DRAM2 - which can bring in any pre-made databases "modules"


Other Project and how they rely on DRAM
	[[NIH-Methylamines]] - methyl compounds - annotations are poor so we have made our own databases and pipelines - NEEDS to be incorporated into DRAM
		Has own pipeline and database (going to be "finished" on June 15th) - [[Dimitri]]
			Probably will be not working
			This pipeline also includes 3 gene sets which need to be called separately because they include stop codons which messes up the annotation
			**need to make a DRAM2 module: "Pyrolysine-gene-caller"**
			

Condensed Tanins - CAMPER - own databases and pipelines - now included in DRAM

EMERGE Team - has own set of databases 



Meeting with [[Rory]] Date: {{2023-06-14}} Time: {{15:00}} : [[Meeting with Rory 06-14-2023]]
	Modularization
		Some are done but not all
			NEED TO DETERMINE THIS
	How to build "packages" i.e. for the Shale database and integrate them into DRAM
	Passwords
		ReadtheDocs
		GitHub
	Location of stuff on the server
	**Need to make list of questions for Rory**: [[List of Questions for Rory]]


Plan for DRAM:
	Meet with Rory Date: {{2023-06-14}} Time: {{15:00}}: [[Meeting with Rory 06-14-2023]]
	Work 3 days a week on DRAM (60%)
	Work on other pipelines other days (40%)
	Meet with DRAM team and outline what works and doesn't work: [[DRAM2 Group Meeting July 14 2023]]
		Usually little things they have
		This team also will test anything I need them to
	



[[Wetlands]] Pipeline/Project
	Timeline: this needs to be done by: August (but the priority is DRAM)
	Goals
		MAGs database
		Write pipeline in Snakemake or Nextflow
	Overview
		Input: 120 metaG samples
			reads
			QC - megahit or idba
			assembly - metabat2
			bins - checkm/checkm2
			QC - med/high filter

These go into GROW database
Want - to take new input reads and before going to the pipeline is to map these reads to the database, i.e. GROW or MUCC, and pull out these reads and jsut assemble what is left
We can set a cutoff for how many of the reads map to the database (GROW or MUCC), for example 90%, and then not assemble these.

Say you don't have a database, you will just assemble all of the reads into metagenomes and you get MAGS and this is now the new database.
	Take these MAGS and map the raw reads to the generate MAGS
		Then iteratively assembly until you run out of bins. Either bins are low or the reads left over are a small amount. 


3 options to run the pipeline as:
1. new data and just make a new MAG database
	1. still choose assembler (IDBA or Megahit)
2. new data with iterative
	1. run pipeline and iterative happens on the generated MAG database
			1.needs to know when to stop the iteration (i.e. stop at 5 MAGs or 15Gbp)
3. New data with existing database
	1. input new data and database
	2. pulls out reads which map to the given database and then at the end, adds the MAGs to the new database
	3. Option to add new MAGs to the given database or to not add them
	4. For mapping you want to map reads that are semi-perfect i.e. 99%
		1. But for a given Bin, they would need like 90% of reads mapped to it to be excluded

At the end, you can take everything that didn't map and try to 
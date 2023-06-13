## Goal: 
1. Goal of the pipeline is to take in raw reads and to generate MAGs
2. Also, there will be 3 different options which the user can chose from to run the pipeline
	1. These are outlined below
	2. In short, a user can just generate all the MAGs which can be generated from the reads. However, to speed up the process the user can specify a database to first map the reads to. These reads will then be discarded and the output will include which MAGs from the given database were identified. Then, the remaining reads will go through the pipeline to generate MAGs. Another option is for the user to chose to iterate on the MAGs. This is something I do not understand yet.



## Pipeline Overview
Pipeline overview: (first went over in [[Meeting with Kayla 06-12-2023]])
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


## Unknowns/Questions
1. I am not sure yet what the "iterative" part is for option 2 of the pipeline.
2. ....lots of other stuff to keep adding
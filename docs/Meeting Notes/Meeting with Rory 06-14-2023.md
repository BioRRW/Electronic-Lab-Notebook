---
title: Meeting with Roary 06-14-2023
allDay: true
date: 2023-06-14
completed: null
---

## Questions for Roary
1. Passwords
	1. GitHub
	2. ...
	3. ...
	4. ...
2. Where is stuff on the server
	1. Walk me through the directories for both DRAM and DRAM2
		1. ..
3. How did you typically work on DRAM and DRAM2
	1. i.e. did you mainly work on the server to test stuff?
		1. ..
	2. Do you have a version on your local machine to run and test stuff?
		1. ..
4. Things you Love about DRAM
	1. ...
5. Things you Hate about DRAM
	1. ...
6. Things you Love about DRAM2
	1. ...
7. Things you hate about Dram2
	1. ...



## Stuff I want to go over
1. Walk me through how DRAM works from start to finish
2. Same with DRAM2, walk me through DRAM2
3. 


## Current state of DRAM2
- DRAM2 has individual commands (apps), some of which are the same from DRAM but some which are separated
	- i.e. DRAM: `DRAM.py annotate` in DRAM2: `dram2 .. call` and `dram2 annotate` 
- Which of these have been implemented and which have not been
	- Implemented
		- ...
		- ...
	- Not done
		- ...
		- ...
- These seem to be written in the GitHub DRAM2/dram2/
	- Which has:
		- annotate
		- auto_protocol
		- call_genes
		- distill
		- genbank
		- strainer
		- ....
	- These each have their own `__init.py__` script along with (sometimes) some associated .py scripts
	- It seems each of these are the "modules" and are invoked with the `dram2 ____ `
		- 
## Snakemake????
1. Show me the "config" file for Snakemake
2. Explain how it runs and manages resources
	1. Are the resources tunable by the user (Can show Nextflow config for reference)
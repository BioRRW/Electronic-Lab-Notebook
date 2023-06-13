
# DRAM
- Dram v1.4.4 still being used by some people
- However, most people are switching over to DRAM2 however, it does not have all of the functionality, yet.


![[Pasted image 20230613091913.png]]


## Implementation
- Written in Python

## Databases
- [KEGG](https://www.kegg.jp/) (if provided by the user), [UniRef90](https://www.uniprot.org/), [PFAM](https://pfam.xfam.org/), [dbCAN](http://bcb.unl.edu/dbCAN2/), [RefSeq viral](https://www.ncbi.nlm.nih.gov/genome/viruses/), [VOGDB](http://vogdb.org/) and the [MEROPS](https://www.ebi.ac.uk/merops/) peptidase database as well as custom user databases
- 

## Dependencies
- [pandas](https://pandas.pydata.org/), [networkx](https://networkx.github.io/), [scikit-bio](http://scikit-bio.org/), [prodigal](https://github.com/hyattpd/Prodigal), [mmseqs2](https://github.com/soedinglab/mmseqs2), [hmmer](http://hmmer.org/) and [tRNAscan-SE](http://lowelab.ucsc.edu/tRNAscan-SE/)
	- *This is if you do not use the Conda install*

## Candidate installation
- This is if you want the latest version which is not typically pushed to Pypi or Bioconda
```
# Clone the git repository and move into it
git clone https://github.com/WrightonLabCSU/DRAM.git
cd DRAM
# Install dependencies, this will also install a stable version of DRAM that will then be replaced.
conda env create --name my_dram_env -f environment.yaml
conda activate my_dram_env
# Install pip
conda install pip3
pip3 install ./
```

## Documentation and Information
- Details on DRAM and how DRAM works please see the [paper](https://academic.oup.com/nar/article/48/16/8883/5884738) as well as the [wiki](https://github.com/WrightonLabCSU/DRAM/wiki).
- For information on how DRAM is changing, please read the most recent [release notes](https://github.com/WrightonLabCSU/DRAM/releases/latest).


## Input/Output
### DRAM (annotate):
**Purpose:** Annotate MAGs; single or multiple

**Input:**
- fasta file or string with wildcards
- Bin taxonomy
	- TSV w/ 1st column being the bins and 2nd column with ‘classification’
	- GTDB-tk output is in this format
- Bin quality
	- TSV w/ 1st column being the bins and 2nd column ‘Completeness’ and 3rd ‘Contamination’
		- This is the output format of checkM
- Output folder
- **Can also supple additional databases
	- These can be HMMs or fastas and have required formats
- **Also need a CONFIG file

**Output:**
- Tab separated file (.tsv) with all the annotations from Pfam, KEGG, UniProt, dbCAN, and MEROPS databases for all genes in all the input genomes
- GenBank files for each genome
- Single gene-finding format (.gff) file of all annotations across genomes
- Single fasta format file (.fasta) of each open reading frame nucleotide sequence and best ranked annotation (see Annotation grades section)
- Single fasta format file (.fasta) of each translated open reading frame amino acid sequence and best ranked annotation KEGG annotation
- Tab separated files (.tsv) with tRNAs and rRNAs

### **DRAM (distill):**
**Purpose:** Summarize annotations (add more)

**Input:**
- annotations.tsv
- output directory
- rrnas.tsv (optional)
- trnas.tsv (optional)

**Output:**
- genome_summary.xlsx
	- summary of metabolisms present in each genome
- genome_statistics.tsv
	- contains all measures required by MIMAG (Minimum Information about a Metagenome-Assembled Genome) about each fasta used as input
- liquor.html
	- interactive HTML for gene pathways
- **Can also provide custom Distill files for specific genes of interest

### **DRAM (strainer):**
**Purpose:** Further gene analysis by making trees of functional modeling

**Input:**
- You need to specify specific identifiers/genes or provide a TSV with specific genes of interest
- annotations.tsv
- input fasta
- output location

**Output:**
- Depends on what you want to do. You can,
	- Pull out a subset of genes to build a tree and get an output \*.faa file
	- Blast specific genes
	- Pull out gene involved in a specific functional category
		- i.e. bins from *Roseburia* genus that are involved in the TCA cycle
			- --taxonomy Roseburia --categories TCA

--------------------------------------------------------------------------

# DRAM2

## Implementation
- Written in Python and SnakeMake
	- Used a config file for running
		- This is on the server for everyone `etc/dram_config.yaml` : [[dram_config.yaml]]
		- However, a user can create their own config file which needs to be located in `~/.config/dram_config.yaml`

Being used for the Workshop and most people are using DRAM2 by the start of the Fall

## Dram2 vs Dram1 (taken from [DRAM2 readthedocs](https://github.com/WrightonLabCSU/DRAM2/blob/main/docs/getting_started/dram1_to_dram2.rst))
- It has a project config that can store run data. This is used for checking, and lets us skip most arguments.
- It has more steps than DRAM1, but each step is simpler.
- DRAM-v is not part of DRAM2. It may be in the future, but not currently.
- There is only one command, dram2 which lets you use all sub commands.
- Only DRAM2 has Adjectives and Phylogenetic Trees.
- Not everything from DRAM1 is implemented in DRAM2 yet.


## How DRAM2 is run
`dram2 <general_options> <sub_command> <sub_command_options> <arguments>`


## Snakemake
- How does snakemake work? 
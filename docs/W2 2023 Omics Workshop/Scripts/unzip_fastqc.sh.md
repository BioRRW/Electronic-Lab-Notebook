```
#!/bin/bash
#SBATCH --nodes=1
#SBATCH --ntasks=2
#SBATCH --time=14-00:00:00
#SBATCH --mem=50gb
#SBATCH --mail-type=BEGIN,END,FAIL
#SBATCH --mail-user=reedrich@colostate.edu
#SBATCH --partition=wrighton-hi,wrighton-low

cd ../raw_reads
gunzip WCRC_304*
fastqc WCRC_304_R1.fastq WCRC_304_R2.fastq
```
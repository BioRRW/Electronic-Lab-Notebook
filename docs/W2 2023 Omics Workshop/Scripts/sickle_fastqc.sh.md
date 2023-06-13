```
#!/bin/bash
#SBATCH --nodes=1
#SBATCH --ntasks=10
#SBATCH --time=14-00:00:00
#SBATCH --mem=100gb
#SBATCH --mail-type=BEGIN,END,FAIL
#SBATCH --mail-user=reedrich@colostate.edu
#SBATCH --partition=wrighton-hi,wrighton-low

cd ../processed_reads
sickle pe -f ../raw_reads/WCRC_304_R1.fastq -r ../raw_reads/WCRC_304_R2.fastq -t sanger -o WCRC_304_R1_trimmed.fastq -p WCRC_304_R2_trimmed.fastq -s R1R2_singles.fastq
# delete the singles file--we dont need it!
rm R1R2_singles.fastq
fastqc WCRC_304_R1_trimmed.fastq WCRC_304_R2_trimmed.fastq
```
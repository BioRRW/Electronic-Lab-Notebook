```
#!/bin/bash
#SBATCH --nodes=1
#SBATCH --ntasks=20
#SBATCH --time=14-00:00:00
#SBATCH --mem=400gb
#SBATCH --mail-type=BEGIN,END,FAIL
#SBATCH --mail-user=reedrich@colostate.edu
#SBATCH --partition=wrighton-hi,wrighton-low

cd ../assembly
megahit -1 ../processed/WCRC_304_R1_trimmed.fastq -2 ../processed/WCRC_304_R2_trimmed.fastq --k-min 31 --k-max 121 --k-step 10 --mem-flag 1 -m 429496729600 -t 20

```
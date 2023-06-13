```
#!/bin/bash
#SBATCH --nodes=1
#SBATCH --ntasks=20
#SBATCH --time=14-00:00:00
#SBATCH --mem=400gb
#SBATCH --mail-type=BEGIN,END,FAIL
#SBATCH --mail-user=reedrich@colostate.edu
#SBATCH --partition=wrighton-hi,wrighton-low

cd ../assembly/megahit_out
/ORG-Data/scripts/quicklooks/contig_stats.pl -i final.contigs.fa -o WCRC_304_final.contigs_STATS
```
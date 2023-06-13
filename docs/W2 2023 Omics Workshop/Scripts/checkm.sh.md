```
#!/bin/bash
#SBATCH --nodes=1
#SBATCH --ntasks=20
#SBATCH --time=14-00:00:00
#SBATCH --mem=200gb
#SBATCH --mail-type=BEGIN,END,FAIL
#SBATCH --mail-user=reedrich@colostate.edu
#SBATCH --partition=wrighton-hi,wrighton-low

cd ../assembly/megahit_out/WCRC_304_final.contigs_2500.fa.metabat-bins
checkm lineage_wf -t 20 -x fa . checkm
cd checkm
checkm qa -o 2 -f results.txt --tab_table -t 20 lineage.ms .
```
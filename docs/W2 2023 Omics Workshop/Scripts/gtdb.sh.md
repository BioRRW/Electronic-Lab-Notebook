```
#!/bin/bash
#SBATCH --nodes=1
#SBATCH --ntasks=20
#SBATCH --time=14-00:00:00
#SBATCH --mem=200gb
#SBATCH --mail-type=BEGIN,END,FAIL
#SBATCH --mail-user=reedrich@colostate.edu
#SBATCH --partition=wrighton-hi,wrighton-low

cd ../MAGs
gtdbtk classify_wf -x fa --genome_dir . --out_dir gtdb_v2.3.0_r214 --cpus 20 --mash_db /home/opt/gtdbtk/data/release214/mash/gtdb_ref_sketch.msh
```
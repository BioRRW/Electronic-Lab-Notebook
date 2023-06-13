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
# pull scaffolds >= 2500 bp
pullseq.py -i final.contigs.fa -m 2500 -o WCRC_304_final.contigs_2500.fa
# map to these scaffolds to get sam file
bbmap.sh -Xmx48G threads=20 overwrite=t ref=WCRC_304_final.contigs_2500.fa in1=../../processed_reads/WCRC_304_R1_trimmed.fastq in2=../../processed_reads/WCRC_304_R2_trimmed.fastq out=WCRC_304_final.contigs_2500_mapped.sam
# convert sam to bam, and sort
samtools view -@ 20 -bS WCRC_304_final.contigs_2500_mapped.sam > WCRC_304_final.contigs_2500_mapped.bam
samtools sort -T WCRC_304_final.contigs_2500_mapped.sorted -o WCRC_304_final.contigs_2500_mapped.sorted.bam WCRC_304_final.contigs_2500_mapped.bam -@ 20
# filter for high quality mapping (this step can be tunable and optional)
reformat.sh -Xmx100g minidfilter=0.99 in=WCRC_304_final.contigs_2500_mapped.sorted.bam out=WCRC_304_final.contigs_2500_mapped99per.sorted.bam pairedonly=t primaryonly=t
#bin
runMetaBat.sh WCRC_304_final.contigs_2500.fa WCRC_304_final.contigs_2500_mapped99per.sorted.bam
```
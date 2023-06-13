1. Ran the copy and rename script and it was super quick!
	This prompted me to make a SLURM folder in my email and auto direct the slurm outputs to this
2. Next I ran the [[unzip_fastqc.sh]] script
	1. This took longer, 29 minutes, mainly because the fastq files are 19G!

| NA | # Reads | Size (Gb) |  
| -------- | -------- |  -------- | 
| R1 b4 trim | 54,616,206 |  19 |
| R2 b4 trim | 54,616,206 | 19 |
| R1 after trim | NA | NA |
| R2 after trim | NA | NA |

R2 Quality across read length from FastQC
![[R2_untrimmed.png]]

R1 adapter content across read length from FastQC
![[Adaptor content R1.png]]

3. Next I ran the trimming using [[sickle_fastqc.sh]]
	1. sickle pe -f ../raw_reads/WCRC_304_R1.fastq -r ../raw_reads/WCRC_304_R2.fastq -t sanger -o WCRC_304_R1_trimmed.fastq -p WCRC_304_R2_trimmed.fastq -s R1R2_singles.fastq
	2. We lost X reads from trimming
	3. **Paste picture** showing the quality and adapter content


| NA | # Reads | Size (Gb) |  
| -------- | -------- |  -------- | 
| R1 b4 trim | 54,616,206 |  19 |
| R2 b4 trim | 54,616,206 | 19 |
| R1 after trim | 54,195,840 | 19 |
| R2 after trim | 54,195,840 | 19 |

![[R1-Trimmed.png]]

![[R1-trimmed-adapter.png]]


4. Next, re-zipped the reads using [[zip_raw.sh]] This frees up 38Gb
	1. How many reads did we lose? **420,366 reads**
	2. Does the number of R1 and R2 reads match? **YES**
	3. Have the quality metrics improved? **YES**
5. Next, I used MEGAHIT to assemble the trimmed reads using the [[megahit.sh]] script:
```
megahit -1 ../processed_reads/WCRC_304_R1_trimmed.fastq -2 ../processed_reads/WCRC_304_R2_trimmed.fastq --k-min 31 --k-max 121 --k-step 10 --mem-flag 1 -m 429496729600 -t 20
```

6. Next, assembly stats were generated using [[assembly_stats.sh]] **insert table below**
	1. How many contigs?
	2. N50 = ?
	3. Longest contig = ?
	4. Where else is this information found?
7. Next, Binning using MetaBat2 using the runMetaBat.sh script: [[map_bin.sh]]
	1. First, scaffolds under 2499 bp were excluded using the pullseq.py script
	2. Then, mapped the trimmed reads to the scaffolds fasta and output a SAM file  using bbmap.sh
	3. Next, converted the SAM into a BAM and then sorted using samtools view and samtools sort
	4. Then, filtered for high quality mapping based on mapping score
	5. Lastly, used runMetaBat.sh to perform the binning
8. Next, Bin QC and taxonomy using checkM
	1. Done using the [[checkm.sh]]
	2. How many HQ and MQ MAGs do you have (based on completion/contamination)?
	3. Are there MAGs with high strain heterogeneity? This measures the percentage of contaminating genes that come from the same lineage. What might this mean?
	4. Did your longest scaffolds bin?
	5. Check HQ/MQ MAGs:
```
awk -F "\t" '{if ($6 >49 && $7 <11) print $1}' results.txt
```


9. Making a MAG database
```
# make MAG directory in your sample metaG folder
mkdir MAGs
cd MAGs
# copy MQ + HQ MAGs to this directory
cp ../assembly/megahit_out/WCRC_304_final.contigs_2500.fa.metabat-bins/bin.13.fa .
cp ../assembly/megahit_out/WCRC_304_final.contigs_2500.fa.metabat-bins/bin.11.fa .
# rename the MAGs
mv bin.13.fa WCRC_304_bin.13.fa
mv bin.11.fa WCRC_304_bin.11.fa
```

10. Evaluating MAG taxonomy uisng GTDB: [[gtdb.sh]]
	1. uses a set of 120 (bacterial) and 55 (archaeal) genes to construct a concatenated gene tree. Then, it uses a MAG's position in the tree relative to defined species to assign taxonomy. The GTDB website is a helpful resource to know for looking up the names.
11. Lasty, for this portion I did a cleanup by removing some stuff:

```
rm assembly/megahit_out/WCRC_304_final.contigs_2500_mapped.sam
rm assembly/megahit_out/WCRC_304_final.contigs_2500_mapped.sorted.bam
rm assembly/megahit_out/WCRC_304_final.contigs_2500_mapped99per.sorted.bam
gzip assembly/megahit_out/WCRC_304_final.contigs_2500_mapped.bam
```
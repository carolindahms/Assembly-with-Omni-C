## Genome assembly with PacBio and Omni-C reads
1. Pre-process reads 
   * Convert Pacbio Revio bam files to fastq with pbtk
   * Asses read-length distribution in R plots
   * Remove adaptors with bbtools and hififilt
2. Count kmers with meryl
   * Get best K with mercury script best_k.sh
3. Assess genome with Genomescope2.0
4. Assemble with Hfiasm in solo mode 
   * run with different -t -s and purging (-l) settings eg -t 15 or 20; -s 0.75, 0.55 or 0.35, -l 1 for light purging
   * run with optimum K (-k)
5. Evaluate hifiasm results
   * compare multiple assemblies with different filters using bbtools script statswrapper.sh
   * BUSCO with different databases for both primary and alternate haplotigs using different databases (e.g. vertebrata and actinopterygii)
   * assembly stats with gfastats
   * Merqury plots and stats based on kmers
6. Purge haplotigs using genomescope stats + evaluate final contig assembly

### Scaffolding
1. Preprocess
   * FastQC
2. Map reads separately with bwa mem following steps from [Dovetail tutorial](https://omni-c.readthedocs.io/en/latest/fastq_to_bam.html) 
3. Record valid ligation events with pairtools 
4. Sort pairsam 
5. Mark duplicates
6. Generate bam
7. Quality control of mapped Hi-C reads
8. Scaffolding with YaHS
9. Quality control of scaffolds
   * gfastats and QUAST
10. Omni-C contact maps
11. Check final assembly for contaminants
   * Clean assembly with NCBI FCS for adaptors and contaminants




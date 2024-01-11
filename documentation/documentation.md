# Preparing input files

Collect all relevant input files in [input](../input).

* [Synechocystis_v2_trimmed.fasta](../input/Synechocystis_v2_trimmed.fasta) is the library of used sgRNAs
* [samplesheet_CRISPRi_Lys.csv](../input/samplesheet_CRISPRi_Lys.csv) gives which sample is which
* the respective .fastq.gz files are collected in the folder (../input/fastq)[../input/fastq] and are the output of a sequencing run on a NextSeq 2000 system.

# nf-core-crispriscreen parameter decisions

Pipeline commit used for analysis: [c7c6563eb269bc3426e7481a8324788bc1006306](https://github.com/MPUSP/nf-core-crispriscreen/commit/c7c6563eb269bc3426e7481a8324788bc1006306) from 25th May 2023

Try once with limma normalization and once without. Command for run without limma normalization: 

```
conda activate env_nf
nextflow run ../../pipelines/nf-core-crispriscreen/ -profile singularity --input "input/samplesheet_CRISPRi_Lys.csv" --fasta "input/Synechocystis_v2_trimmed.fasta" --outdir "results" --three_prime_adapter ^CAGTGATAGAGATACTGGGAGCTA...GTTTTAGAGCTAGAAATAGCAAGTTAAAATAAGGC --filter_mapq=1 --max_cpus 5 --max_memory 12GB --run_mageck true --gene_fitness true
```

Command for run with limma normalization:

```
conda activate env_nf
nextflow run ..pipelines/nf-core-crispriscreen/ -profile singularity --input "input/samplesheet_CRISPRi_Lys.csv" --fasta "input/Synechocystis_v2_trimmed.fasta" --outdir "results_limmaNormalization" --three_prime_adapter ^CAGTGATAGAGATACTGGGAGCTA...GTTTTAGAGCTAGAAATAGCAAGTTAAAATAAGGC --filter_mapq=1 --max_cpus 5 --max_memory 12GB --run_mageck true --gene_fitness true --normalization true
```

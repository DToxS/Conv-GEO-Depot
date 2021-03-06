# Analyzing Conventional Random-Primed mRNA-Sequencing Data

This is a computational pipeline designed for analyzing the raw *FASTQ* data files generated from the conventional random-primed mRNA-sequencing method and generating a set of differentially expressed genes (DEGs) for each drug treatment and each cell line.

## Software Requirements

The computational pipeline requires the following software programs:

- *Bash* shell in Unix-like operating systems (e.g. Linux, MacOS, Unix)
- *STAR* (>= v2.5.3a)
- *featureCounts* (from *Subread* >= v1.6.2)
- *R* (>= v3.0.0) with the following packages:
  - *cluster*
  - *edgeR*
  - *gplots*
  - *graphics*
  - *matrixStats*
  - *methods*
  - *RColorBrewer*
  - *stats*
  - *tools*

## Data Preparation

The computational pipeline requires a list of input datasets and a tree structure of data directories.

### Data List

The input datasets for the computational pipeline include:

- A set of compressed mRNA-sequencing *FASTQ* data files (`*.fastq.gz`)
- The experiment design file `Conv-RNAseq-Experiment-Design.tsv.gz`
- The *UCSC* human genome reference library `Reference-Library.tar.gz`
- The data analysis programs `Program-Source-Codes.tar.gz`
- The configuration file for the differential comparison analysis `Differential-Comparison-Configs.tar.gz`
- The parameter files for the differential comparison analysis `Differential-Comparison-Params.tar.gz`

### Data Preparation

Before launching the computational pipeline, a directory tree with corresponding data files needs to be created in the following steps:

1. Create a top directory `Conv-GEO-Depot` with the following tree structure:
   ```
   Conv-GEO-Depot
   ├── Seqs
   ├── Aligns
   ├── Counts
   ├── References
   ├── Programs
   ├── Configs
   ├── Params
   └── Scripts
   ```
2. Place all gzipped *FASTQ* data files in the `Seqs` directory. 
3. Extract the following compressed data files into corresponding directories:
   - Extract `Conv-RNAseq-Experiment-Design.tsv.gz` into the `Counts` directory.
   - Extract `Reference-Library.tar.gz` into the `References` directory.
   - Extract `Program-Source-Codes.tar.gz` into the `Programs` directory.
   - Extract `Differential-Comparison-Configs.tar.gz` into the `Configs` directory.
   - Extract `Differential-Comparison-Params.tar.gz` into the `Params` directory.

## Analysis Workflow

The workflow of this computational pipeline for analyzing the conventional mRNA-sequence data includes the following steps:

### Sequence Alignment

Refer to the [Sequence Alignment](https://github.com/DToxS/Sequence-Alignment) section.

### Feature Counts

Refer to the [Feature Counts](https://github.com/DToxS/Feature-Counts) section.

### Differential Comparison

Refer to the [Differential Comparison](https://github.com/DToxS/Differential-Comparison) section.

## Result Data

- A table of uniquely aligned sequence reads for all reference genes and all sequenced samples `Conv-RNAseq-Read-Counts.tsv` in the `Counts` directory (compressed as `Conv-RNAseq-Read-Counts.tsv.gz`).
- A set of statistical comparison result files for the DEGs identified at all drug treatments and in all cell lines with a file name pattern of `Human-[Cell Line]-Hour-48-Plate-[Plate Number]-Calc.CTRL-[Drug Name].tsv`, located in the `Results/FDR-[Value]` directory under the `Conv-GEO-Depot` top directory.


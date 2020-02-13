# Analyzing Conventional Random-Primed mRNA-Sequencing Data

This is a computational pipeline designed for analyzing the raw *FASTQ* data files generated from the conventional random-primed mRNA-sequencing method and generating a set of differentially expressed genes (DEGs) for each drug treatment and each cell line.

## Software Requirements

The computational pipeline requires the following software programs:

- *Bash* shell in Unix-like operating systems (e.g. Linux, MacOS, Unix)
- *STAR* (version 2.5.3a)
- *featureCounts* (from *Subread* v1.6.2)
- *R* (version >= 3.0.0) with the following packages:
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

- A set of compressed mRNA-sequencing *FASTQ* data files (**.fastq.gz*)
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
    ├── Scripts
    └── Results
    ```

2. Place all gzipped *FASTQ* data files in the `Seqs` directory. 

3. Extract the following compressed data files into corresponding directories:

    - Extract `Conv-RNAseq-Experiment-Design.tsv.gz` into the `Counts` directory.
    - Extract `Reference-Library.tar.gz` into the `References` directory.
    - Extract `Program-Source-Codes.tar.gz` into the `Programs` directory.
    - Extract `Differential-Comparison-Configs.tar.gz` into the `Configs` directory.
    - Extract `Differential-Comparison-Params.tar.gz` into the `Params` directory.

4. Set the variable `DATASET_DIR` in all shell scripts (**.sh*) and the variable `dataset_dir` in the *R* program `Convert-Conv-RNAseq-Reads.GEO.R` under all the sub-directories of the `Programs` directory to the absolute path of the `Conv-GEO-Depot` top directory.

## Analysis Workflow

The workflow of this computational pipeline for analyzing the conventional mRNA-sequence data includes the following steps:

### Sequence Alignment

Refer to the `README` file of the <u>Sequence-Alignment</u> section.

### Feature Counts

Refer to the `README` file of the <u>Feature-Counts</u> section.

### Differential Comparison

Refer to the `README` file of the <u>Differential-Comparison</u> section.

## Result Data

- A table of uniquely aligned sequence reads for all reference genes and all sequenced samples `Conv-RNAseq-Read-Counts.tsv` in the `Counts` directory (compressed as `Conv-RNAseq-Read-Counts.tsv.gz`).
- A set of statistical comparison results for DEGs for all drug treatments and all cell lines `Human-[Cell Line]-Hour-48-Plate-[Plate Number]-Calc.CTRL-[Drug Name].tsv` in the `Results/FDR-[Value]` directory (compressed as `DEG-Calc-FDR-0.1.tar.gz`).
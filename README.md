# Replication Materials: Roberts et al. STM for Open-Ended Survey Responses

This repository contains replication materials for a Structural Topic Model (STM) analysis based on Roberts et al's (2014) paper. 

A link to the original paper can be found here: [https://onlinelibrary-wiley-com.proxy1.lib.uwo.ca/doi/10.1111/ajps.12103]
The purpose of this project is to reproduce key figures and analytical steps from the original paper while documenting the workflow and challenges of replicating STM analyses using the modern `stm` package in R.

## Overview

This replication reconstructs the authors’ STM workflow using the original replication materials where available. The project focuses on:

- Estimating STM models using pre-processed text data  
- Interpreting topic content and structure  
- Reproducing exemplar text figures  
- Estimating treatment and interaction effects  
- Comparing replicated outputs to the original results  

Because the original analysis relied on an earlier version of STM and helper functions that are no longer fully available, this replication emphasizes **substantive similarity** rather than exact numerical reproduction.

## Code

The replication script is:

scripts/gadarian_replication.Rmd

This file contains the full workflow, including:

- Loading required packages and setting the working directory  
- Preparing document-term data and metadata  
- Estimating STM models using `stm()`  
- Selecting a model based on similarity to published results 
- Inspecting topics using `labelTopics()`  
- Extracting example documents using `findThoughts()`  
- Estimating topic prevalence effects using `estimateEffect()`  
- Recreating figures using both built-in STM tools and custom plotting functions where it was required due to uncertainty regarding original methods.

Some figures were recreated using custom functions because the original helper functions referenced in the paper were not available.

### Model Selection

STM produces different results across runs due to local mode variation. As a result, model selection in this replication was based on how closely topic composition and effect plots matched the published figures, rather than exact duplication.

## Data

The data used in this replication is stored in:

data/
├── original_replication_files/   

- `original_replication_files/` contains the original datasets provided by the authors  

These files include:
- document-term matrices  
- vocabulary files  
- metadata associated with each document
- original figures and tables

### Data Limitations

Some components of the replication materials (particularly those associated with the RAND experiment) did not align cleanly across documents, vocabulary, and metadata. Because of these inconsistencies, certain figures could not be fully reproduced.

## Output

Generated figures and outputs are stored in:

output/
├── figures/  

Figures are also generated directly within the `.Rmd` workflow script. 

## Report

The final replication report and presentation materials are located in:

report/

## Main Replication Challenges

### 1. Outdated STM workflow

The original paper relied on helper functions (e.g., older plotting utilities) that were not recoverable in a usable form. These had to be replaced with updated STM functions or custom code.

### 2. Package version differences

The current `stm` package differs from the version used in the original analysis. This affects:
- model estimation  
- available functions  
- plotting workflows  

### 3. Local mode variation

STM is sensitive to initialization and optimization paths. Even with fixed seeds, results vary across runs and machines. This makes exact replication difficult.

### 4. Data inconsistencies

Some datasets, particularly in the Rand and ANES experiments, contained mismatches across files. These prevented full reconstruction of parts of the analysis.

## How to Run the Replication

1. Open `scripts/gadarian_replication.Rmd` in RStudio  
2. Install required packages:

```r
install.packages(c("stm", "tidyverse", "knitr"))

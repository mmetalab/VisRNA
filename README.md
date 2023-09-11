# VisRNA
# Abstract
# Motivation: 
Non-small cell lung cancer (NSCLC) constitutes a significant proportion of lung cancer cases and is a leading global cause of death. Single-cell RNA sequencing (scRNA-seq) has emerged as a potent tool for elucidating disrupted genes and mechanisms at the single-cell level, offering insights into discovering therapeutic targets for NSCLC.
# Results: 
This study introduced VisRNA, a Python-based visualization web application tailored for efficient statistical and functional analysis using scRNA-seq data. VisRNA employs machine learning for multiple-dimensionality reduction techniques for scRNA-seq data and subsequent automatic cell-type annotation. By analyzing the differentially expressed genes among different cell clusters, VisRNA identified putative therapeutic targets and drug candidates, ranked by the results of the molecular docking simulation. VisRNA integrated NSCLC scRNA-seq data, uncovering 14 cell types with significantly differentially expressed genes. Notably, the potential drug dihydroergotamine emerged, exhibiting the lowest binding affinity for different targets across multiple cell types, indicating potential therapeutic targets and drug candidates for NSCLC.

# Steps to run VisRNA locally

## Install core data analysis and visualization packages via pip
Run 'pip install streamlit pandas numpy seaborn matplotlib sklearn' at the command line to install the necessary packages. Streamlit builds the web app, pandas and numpy support data manipulation and math operations, seaborn and matplotlib enable statistical plotting and visualization, sklearn provides machine learning algorithms for dimension reduction and clustering. These core packages need to be installed prior to importing and using them.

## Import key packages for data analysis, visualization, and web app building
Streamlit is imported as 'st' to build the interactive web app with Python. Pandas and numpy are imported as 'pd' and 'np' to provide fast, flexible data structures and support numerical computing. Seaborn and matplotlib are imported as 'sns' and 'plt' to allow creation of insightful statistical graphics and plots for exploratory data analysis and visualization. The sklearn modules PCA and TSNE are imported for implementing dimension reduction techniques like principal component analysis and t-SNE that project high-dimensional data into lower dimensions for plotting. 

## Activate conda environment containing required dependencies
Execute 'conda activate visrna' at the command line to switch into the 'visrna' conda environment. This env contains all the necessary package dependencies in the right versions needed to successfully run the streamlit data analysis scripts. Activating the environment ensures you are using the correct packages. Environments provide isolation from other projects.

## Set working directory to folder containing scripts 
Use the 'cd' command to change the current working directory to the folder path where the Python scripts are located, e.g. 'cd /path/to/scripts'. This allows you to easily run the scripts without needing to specify the full absolute file path each time. It also ensures any output is saved to the correct location.

## Run script 1 to load, process, and normalize gene expression data 
Execute 'streamlit run 01_💡VisRNA.py' to run the first script. This script loads in the raw gene expression matrix data, applies filtering to extract highly variable genes, normalizes the data using log-normalization to account for outliers, and scales the data using standard scaling/Z-scoring to center and standardize values for comparable ranges. The output is a processed gene expression matrix suitable for downstream analysis.

## Run script 2 to load preprocessed gene expression matrix
Call 'streamlit run 02_📝Load_data.py' to run the second script. This script loads the normalized and scaled gene expression matrix output from script 1 into memory to be used for subsequent analysis like dimension reduction and clustering. It reads in the processed data.

## Run script 3 for dimension reduction and data visualization
Execute 'streamlit run 03_📉Dimension_reduction_visualization.py' to run the third script. This script takes the preprocessed data loaded by script 2 and applies PCA and t-SNE dimension reduction algorithms from scikit-learn to reduce the high dimensional data down to 2 dimensions for easy visualization. It outputs 2D projections of the data.

## Run script 4 for cell clustering and type annotation
Call 'streamlit run 04_🧬Cell_type_annotation.py' to run the fourth script. This script performs clustering analysis like k-means on the dimension reduced data from script 3. It then annotates clusters with known cell type labels based on correlation of marker gene expression signatures, enabling biological interpretation of the cell groupings.

## Run script 5 for differential expression analysis
Execute 'streamlit run 05_📊Differential_gene_analysis.py' to run the fifth and final script. This script identifies genes differentially expressed between the annotated cell types from script 4. It outputs lists of marker genes upregulated or downregulated in each cell type.

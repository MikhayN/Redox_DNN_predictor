# Redox_DNN_predictor
Redox-sensitive protein predictor, based on Deep Neural Network

## Motivation
Prediction of redox active proteins is important for analysis of redox signaling pathways.

## Data
Model is created with cross-reference on [OxICAT data](https://panoramaweb.org/project/Panorama%20Public/2018/Warscheid%20Lab%20-%20yeast_oxICAT/begin.view?) from [an article](https://www.nature.com/articles/s41467-017-02694-8)

Model is evaluated on [data](https://biocomputer.bio.cuhk.edu.hk/RSCP/) from [an article](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-016-1185-4)

## NN platform
The predictor is implemented on F# with Microsoft Cognitive Tool (CNTK). As a base for implementation the code of [Mathias Brandewinder](https://github.com/mathias-brandewinder/CNTK.FSharp) was used, as well as [general tutorial](https://courses.edx.org/courses/course-v1:Microsoft+DAT236x+1T2019a/course/) for creating different NN-architectures with CNTK.

## Problem formulation and NN architecture
1. Feature feeding

   Extract features out of the protein sequence for each Cysteine residue and use them as input value for the NN.  
   Set level of oxidation of a Cysteine as a corresponding output.  
   Use an architecture of vanilla Neural Network with several hidden layers

2. Sequence feeding

   Break the whole protein sequence into peptides such that there were peptides from experiment (containing active Cysteine residue) and rest of the sequence and use them as sequential input value for the NN.  
   Set level of oxidation of a Cysteine as a corresponding output for Cys-containing peptide or 0 otherwise.  
   Use an architecture of Recurrent Neural Network with first set of layers for peptide2word embedding.


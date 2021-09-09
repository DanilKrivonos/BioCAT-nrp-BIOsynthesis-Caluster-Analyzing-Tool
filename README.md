# BioCAT: Biosynthesis Cluster Analysis Tool
<img src="https://user-images.githubusercontent.com/53526550/132544644-86306499-133d-44e2-8e4c-e2603fb7d0f0.png" width="205" height="145" align="left">BioCAT is a tool which is designed for searching potential producers of a given non-ribosomal peptide. The tool performs an alignment of the given NRP chemical structure against all possible biosytnthesis gene clusters (BGCs) found in the given genome and returns the final alignment score distributed from 0 to 1. Alignments with score higher than 0.5 can be considered as successful matches.

Identification on monomers graph is performed with the rBAN tool(https://jcheminf.biomedcentral.com/articles/10.1186/s13321-019-0335-x). Annotation of nonribosomal peptide synthetase gene clusters is preformed with the antiSMASH 6 software(https://academic.oup.com/nar/article/49/W1/W29/6274535).
## **Dependencies:**
- antiSMASH 6.0.0

rBAN is included into the BioCAT package.

### python3 libraries:
- sklearn 0.24.2
- pandas 1.2.5
- biopython 1.79
- numpy 1.21.0
- rdkit 2021.03.4
## **Installation:**
```git clone https://github.com/DanilKrivonos/BioCAT```

## **BioCAT usage:**
### Usage example:
```
python3 BioCAT.py -smiles '[H][C@@]1(CCC(O)=O)NC(=O)CC(CCCCCCCCCCC)OC(=O)[C@]([H])(CC(C)C)NC(=O)[C@@]([H])(CC(C)C)NC(=O)[C@]([H])(CC(O)=O)NC(=O)[C@@]([H])(NC(=O)[C@@]([H])(CC(C)C)NC(=O)[C@]([H])(CC(C)C)NC1=O)C(C)C' -name 'surfactin' -genome example/Surfactine/GCF_000015785.2_ASM1578v2_genomic.fna -out surfactin_results 
```

In this case, the chemical structure of surfactin given in the SMILES format is processed by rBAN and the genome is processed by antiSMASH 6. Next, resulting files are used for the alignment process. The main feature of BioCAT is PSSM-based alignment algorithm, which includes an artifitial shuffling of PSSMs to calculate the final score, so, the alignment process might be time-consuming in some cases (usualy less than 1 minute). 

The output directory contains the rBAN and the antiSMASH resulting files, PSSM matrices for BGCs which were aligned during the analysis, and the resulting file `Results.tsv`.
This file contains a detailed information about each possible NRP to BGC alignment, but now we are interested only in the last two columns `Relative score' and `Binary`. Rows with relative score more than 0.5 are interpreted as successful alignments, thus, the given organism can be considered as a potential producer of surfactin.

### Parameters

will be added

## Reference

will be added
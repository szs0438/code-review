# Code Review:Soybean Expression Atlas v2

**Paper:** The Soybean Expression Atlas v2: A comprehensive database of over 5000 RNA-seq samples  
**DOI:** https://doi.org/10.1111/tpj.16459  
**Code Repository:** https://github.com/almeidasilvaf/SEA_paper

I will review the code associated with this paper, which processes and analyzes over 5000 RNA-seq samples from soybean. The code is written 
in R using Quarto documents and a companion R package called `bears`.
---

## 1. Summary

This paper presents the Soybean Expression Atlas v2, a large-scale RNA-seq database containing transcript- and gene-level abundance matrices for 5,481
publicly available RNA-seq samples from soybean (*Glycine max*). The updated atlas is a fourfold increase over the original version and introduces new
features including transcript-level abundance estimates, bias-corrected counts, and a redesigned web interface. The authors also developed a companion Rpackage called `bears` to make the RNA-seq processing pipeline more reproducible and
scalable.

As requested by the editor, my review below focuses on the code associated with this manuscript, available at https://github.com/almeidasilvaf/SEA_paper.

---
## 2. High-Level Feedback

The repository is publicly available on GitHub,The repository contains a main README.md, a folder called `chapters/` with six numbered Quarto (.qmd) analysis scripts, a `data/` folder, and a `products/` folder for outputs. The use of an `SEA_paper.Rproj` R Project file is good practice for managing filepaths across computers.

However, a new user immediately faces a major barrier: there are no instructions in the README explaining how to install the required R packages.
The analysis depends on a companion R package called `bears`, but this is never mentioned with installation instructions. The README should include
something like:

### Install the bears package

```
remotes::install_github("almeidasilvaf/bears")
```

The code also depends on external command-line tools `fastp` and `salmon` for quality control and transcript quantification, but no installation guidance is provided for these tools either.

### 2.2 Reproducibility

Full reproduction of results is not realistic for most users for three reasons. First, running the pipeline requires downloading potentially terabytes of raw RNA-seq data from NCBI, and no small example dataset is provided for testing. 
Second, in `01_creating_the_SEA_v2.qmd`, the authors write that a file "was manually edited" outside of the code — this step cannot be reproduced by
anyone else and is a serious reproducibility problem. Third, no `renv.lock` file is provided to record which exact versions of R and all packages were used.

### 2.3 Git Usage

The repository has only 10 commits total, which is very few for a project of
this scale. Most files were added in a single "Initial commit of new
Quarto-based repo" message, making the development history essentially
invisible. More frequent commits with descriptive messages would greatly
improve transparency and trust in the code.

### 2.4 Documentation

Using Quarto documents is a good choice because it combines readable narrative
text with code in the same file. However, the main README does not explain
what software needs to be installed, how long the pipeline takes to run,
or what each folder in the repository contains.

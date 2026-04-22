# Code Review:Soybean Expression Atlas v2

**Paper:** The Soybean Expression Atlas v2: A comprehensive database of over 5000 RNA-seq samples  
**DOI:** https://doi.org/10.1111/tpj.16459  
**Code Repository:** https://github.com/almeidasilvaf/SEA_paper  
  

---

## 1. Summary

This paper presents the Soybean Expression Atlas v2, a large-scale RNA-seq database containing transcript- and gene-level abundance matrices for 5,481
publicly available RNA-seq samples from soybean (*Glycine max*). The updated atlas is a fourfold increase over the original version and introduces new
features including transcript-level abundance estimates, bias-corrected counts, and a redesigned web interface. The authors also developed a companion Rpackage called `bears` to make the RNA-seq processing pipeline more reproducible and
scalable.

As requested by the editor, my review below focuses on the code associated with this manuscript, available at https://github.com/almeidasilvaf/SEA_paper.

---

## 2. High-Level Feedback

### 2.1 Obtaining and Setting Up the Code

The repository is publicly available on GitHub,The repository contains a main README.md, a folder called `chapters/` with six numbered Quarto (.qmd) analysis scripts, a `data/` folder, and a `products/` folder for outputs. The use of an `SEA_paper.Rproj` R Project file is good practice for managing filepaths across computers.

However, a new user immediately faces a major barrier: there are no instructions in the README explaining how to install the required R packages.
The analysis depends on a companion R package called `bears`, but this is never mentioned with installation instructions. The README should include
something like:

```
# Install the bears package

 remotes::install_github("almeidasilvaf/bears")

```

The code also depends on external command-line tools `fastp` and `salmon` for quality control and transcript quantification, but no installation guidance is provided for these tools either.

### 2.2 Reproducibility

Full reproduction of results is not realistic for most users for three reasons. First, running the pipeline requires downloading potentially terabytes of raw RNA-seq data from NCBI, and no small example dataset is provided for testing. 
Second, in `01_creating_the_SEA_v2.qmd`, the authors write that a file "was manually edited" outside of the code-this step cannot be reproduced by
anyone else and is a serious reproducibility problem. Third, no `renv.lock` file is provided to record which exact versions of R and all packages were used.

### 2.3 Git Usage

The repository has only 10 commits total, which is very few for a project of this scale. Most files were added in a single "Initial commit of new
Quarto-based repo" message, making the development history essentially invisible. More frequent commits with descriptive messages would greatly
improve transparency and trust in the code.

### 2.4 Documentation

Using Quarto documents is a good choice because it combines readable narrative text with code in the same file. 
However, the main README does not explain what software needs to be installed, how long the pipeline takes to run, or what each folder in the repositorycontains.

---

## 3. Specific Code-Level Observations

After visiting the repository and opening `01_creating_the_SEA_v2.qmd`, I found the following specific issues and strengths:

### Problems I found:

- **Undefined variable bug:** The variable `metadata_atlas_v2_downloaded` is used in the `final_metadata_dataframe` code chunk but is never assigned anywhere in the script. If someone ran this code exactly as written, it would fail with an error.

- **Copy-paste error:** The pattern `".*embryo.*" = "embryo"` appears three times in a row inside the `standardize_names` code chunk. This is a copy-paste mistake with no effect, but it shows the code was not carefully checked before publication.
  
- **Manual editing breaks reproducibility:** After generating the file `final_metadata_classified_tissues.tsv`, the authors state it "was manually edited." There is no code documenting what changes were made, so no one else can reproduce this step.

- **No example dataset:** The `data/` folder contains only saved output files. There is no small input dataset that would let a new user test whether the code runs correctly without downloading terabytes of data.

- Neither a conda environment file (environment.yml) nor an R environment lock file (renv.lock) is provided.

### Strengths I found:

- `set.seed(123)` is used at the top of the first script, which is good practice for reproducibility.

- `sessioninfo::session_info()` appears at the end of the script, recording the exact R version and package versions used during the analysis.

- Code chunks have descriptive names like `check_integrity`, `quantify_abundance`, and `standardize_names`, making the document easy
  to navigate.
  
- Variable names throughout the code are clear and descriptive, for example `metadata_atlas_v2_filtered`, `biosamples_to_keep`, and `mapping_rate

---

## 4. Conclusion

The Soybean Expression Atlas v2 code is a genuinely valuable contribution to the plant biology community.The decision to use Quarto documents makes
the analysis readable, and building the processing pipeline into a dedicated R package (`bears`) shows good software design.  `set.seed()`, `sessioninfo()`, descriptive variable names, and numbered chapter files are good coding practices.

However,several issues (the absence of installation and setup instructions in the README, a manual data editing step that cannot be reproduced from codealone) would prevent most users from reproducing the results. If they address those issues would make this resourc more accessible for community of plant scientist.



# Code Review Proposal

**Paper:** The Soybean Expression Atlas v2  
**DOI:** https://doi.org/10.1111/tpj.16459  
**Code Repository:** https://github.com/almeidasilvaf/SEA_paper

I will review the code associated with this paper, which processes and analyzes over 5000 RNA-seq samples from soybean. The code is written 
in R using Quarto documents and a companion R package called `bears`.

# Code Review: Soybean Expression Atlas v2

**Paper:** The Soybean Expression Atlas v2  
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

## 2. Overall Evaluation of the Code
The code provides useful functionality for RNA-seq data analysis, but its usability and clarity could be improved, especially for new users.

---

## 3. Reproducibility

The code is publicly available, but reproducibility is only partially supported. Clear step-by-step instructions and environment setup details are missing, making it difficult for new users to fully reproduce the results.

---

## 4. Documentation
The repository includes a README file, but documentation is limited. More detailed instructions, examples, and explanations of input and output files would improve usability.

---

## 5. Code Quality
The code is functional but could be improved by increasing modularity, using more descriptive variable names, and adding comments to improve readability.

---

## 6. Strengths

- Integrates a large RNA-seq dataset (>5000 samples)  
- Provides a valuable resource for soybean transcriptomics  
- Code is publicly available, promoting transparency  
- Supports large-scale gene expression analysis

---

## 7. Suggestions

- Add step-by-step instructions
- Provide example datasets
- Improve comments and variable naming
- Add environment setup (e.g., conda)

---

## 8. Conclusion

The code is valuable for RNA-seq analysis but would benefit from improved documentation, reproducibility, and usability to make it more accessible to users.

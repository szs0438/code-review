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

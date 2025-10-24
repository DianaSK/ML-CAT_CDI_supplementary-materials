# ML-CAT Supplementary Materials

This repository contains supplementary materials for the article:

**Title:** ML-CAT: Machine Learning–Based Computerized Adaptive Test  
**Authors:** Diana Saker, Haya Salameh, Hila Gendler-Shalev, and Hagit Hel-Or  

**Affiliations:**  
- Diana Saker, Hagit Hel-Or, and Haya Salameh — Department of Computer Science, University of Haifa, Israel  
- Haya Salameh — also with the Department of Cognitive Science, University of Haifa, Israel  
- Hila Gendler-Shalev — Department of Communication Sciences and Disorders, University of Haifa, Israel  

**Contact Emails:**  
- Diana Saker: [dianasaker4@gmail.com](mailto:dianasaker4@gmail.com)  
- Hagit Hel-Or: [hagit@cs.haifa.ac.il](mailto:hagit@cs.haifa.ac.il)  
- Haya Salameh: [haya.salami@gmail.com](mailto:haya.salami@gmail.com)  
- Hila Gendler-Shalev: [hilags2@gmail.com](mailto:hilags2@gmail.com)  

**Funding:** This work was supported in part by the University of Haifa Data Science Research Center.

**Journal:** Journal Of Biomedical & Health Informatics From IEEE EMBS, 2025  
---

## Abstract

Early identification of infants and toddlers at risk for developmental disorders can improve the efficiency of early intervention programs and reduce healthcare costs. The MacArthur-Bates Communicative Development Inventory (MB-CDI) is a standardized tool for assessing children’s early lexical development. However, due to its long list of words, administration is time-consuming and often limiting.  

In this paper, we use machine learning together with a computerized adaptive testing approach (ML-CAT) to shorten the MB-CDI by adapting the sequence of words to the subject's responses. ML-CAT can reliably predict the final score of the H-MB-CDI with as few as 10 words on average while maintaining 94–96% accuracy.  

ML-CAT outperforms existing approaches, including fixed non-adaptive methods and statistical models based on Item Response Theory (IRT). Results are also provided for five different languages. Most importantly, ML-CAT outperforms IRT-based methods when handling atypical talkers (outliers).  

The ML-CAT enables more efficient lexical development assessment, allowing for wider and repeated screening in the community. Additionally, due to its shorter length, assessment is expected to be less of a burden on the subject or her caregiver and consequently more reliable.

---

## Appendix Materials

### 1. List of Words

The top 50 words for the **Understood** (`DS_u`) and **Produced** (`DS_p`) datasets, with Hebrew transliteration and English translation, are provided in [`appendix/list_of_words.pdf`](appendix.pdf, page 1).  

*(Example rows)*

| Ranking | Understood (Hebrew) | English | Produced (Hebrew) | English |
|---------|--------------------|---------|-----------------|---------|
| 1       | Mzlg               | fork    | llcht           | go      |
| 2       | svvn               | soap    | shmchh          | blanket |
| ...     | ...                | ...     | ...             | ...     |

---

### 2. Figures

- [`appendix.pdf, page 2) — Function fitting that maps estimated ability to CDI score (0–full CDI words).  

---

### 3. Comparative Models Implementation

To benchmark ML-CAT:

- **IRT-CAT:** A computerized adaptive testing model based on Item Response Theory. Adapted from Grzegorz Krajewski and P. Król’s code. Computes subject ability and maps outputs to CDI scores using a sigmoid function.  
- **IRT-CAT Bayes:** Bayesian approach to IRT using MCMC sampling. Based on e-Babylab ([GitHub link](https://github.com/lochhh/e-Babylab.git)) and modified for this study.  

Source code for our implementations:  
- IRT-CAT: `git@github.com:DianaSK/CAT-IRT.git`  
- IRT-CAT Bayes: `github.com/DianaSK/Baysian-IRT`

**Score Mapping Equations:**

The estimated CDI score is computed from the ability parameter θ as follows:

**Understood dataset:**
EstimatedScore_understood(θ) = 428.803 / (1 + exp(-1.6218 * (θ - 0.0114))) + 1.9013  

**Produced dataset:**
EstimatedScore_produced(θ) = 424.713 / (1 + exp(-1.8922 * (θ - 0.3288))) - 1.1762 

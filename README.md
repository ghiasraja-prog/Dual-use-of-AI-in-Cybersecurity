# Bibliometric Analysis — AI in Offensive and Defensive Cybersecurity

Reproducible code for the quantitative analysis reported in **Chapter 4, Sections 4.1–4.3** of a systematic literature review on the dual use of artificial intelligence in cybersecurity.

**Module:** BUSI 1783 — Business Analytics Project

---

## What this repository contains

`bibliometric_analysis.ipynb` reproduces every quantitative figure in Chapter 4:

| Output | Reported in |
|---|---|
| Publications per year, Poisson growth model (IRR) | Section 4.1 |
| Conference vs journal split, citation statistics | Section 4.1, Table 4.1 |
| Term prevalence across title/abstract/keywords | Section 4.2, Figure 4.2 |
| Keyword co-occurrence and weighted-degree centrality | Section 4.2 |
| Orientation distribution (189 eligible, 20 selected) | Section 4.3, Table 4.2, Figure 4.3 |
| Figures 4.1, 4.2, 4.3 | Chapter 4 |

## Scope — what the code does and does not do

**The code counts and plots. It does not produce the findings.**

Every screening decision, orientation code (offensive / defensive / dual-use), quality-based exclusion and thematic interpretation was a **human judgement**, recorded in the screening spreadsheet. The notebook reads those judgements and tabulates them; it does not generate them.

The thematic synthesis reported in **Sections 4.4–4.6 was carried out manually**, without coding software, as stated in Methodology Section 3.8. There is deliberately no code for it in this repository.

## Folder structure

```
.
├── bibliometric_analysis.ipynb    # the analysis
├── requirements.txt
├── data/
│   ├── Scopus_209_Title_Abstract_Screening.xlsx   # 209 screened records + manual decisions
│   └── scopus_export.ris                          # raw 12,500-record Scopus export
└── outputs/                        # figures written by the notebook
    ├── figure_4_1.png
    ├── figure_4_2.png
    └── figure_4_3.png
```

## Running it

```bash
pip install -r requirements.txt
jupyter notebook bibliometric_analysis.ipynb
```

Run all cells top to bottom. The final cell prints a summary table of every value that appears in Chapter 4, so the chapter and the code can be checked against each other in one place.

## Key results

| Measure | Value |
|---|---|
| Raw Scopus search | 12,500 records |
| After document-type and date filters (2014–2024) | 209 |
| Reached full-text assessment | 207 |
| Met all five eligibility criteria | 189 |
| Selected for thematic synthesis | 20 |
| Publication growth | IRR 1.90/year (95% CI 1.72–2.09), p < 0.001 |
| Document types | 138 conference (66.0%), 71 journal (34.0%) |
| Citations | median 7, mean ≈30 |
| Orientation (eligible pool) | 166 defensive, 19 dual-use, 4 offensive |
| Defensive + dual-use : offensive | ≈46 to 1 |

## Notes on the data

- **Citation counts** are recovered from the RIS export by DOI matching. 167 of the 209 screened records matched, so citation statistics are computed on that subset and are reported as approximate.
- **Keyword counts** use the keyword field as supplied in the screening export, which combines author keywords and Scopus index terms. Restricting to author keywords alone would produce lower counts.
- **Term prevalence** counts are non-exclusive: one record can contain several terms, so they do not sum to 209.
- The Poisson IRR measures growth in the **literature captured by this search query**, not growth in cyber attacks.

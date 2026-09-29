---
output:
  pdf_document: default
  html_document: default
---
# Project 2 — Data and source materials

Working topic: **Traditional and Digital Financial Literacy: Should They Be Reported Together or Separately?**

Downloaded from official sources on 16 September 2026. No analysis code has been created yet.

## Primary data

Source page: [Banca d'Italia — Financial literacy of Italian adults](https://www.bancaditalia.it/statistiche/tematiche/indagini-famiglie-imprese/alfabetizzazione/index.html?com.dotmarketing.htmlpage.language=1)

The 2023 IACOFI survey covers 4,862 Italian residents aged 18–79 and contains 219 variables. It includes the first Italian IACOFI measurement of digital financial literacy. The survey weight is `wght`.

- `data/raw/stata/Database_ENG.dta` — preferred working file because it preserves Stata variable and value labels.
- `data/raw/ascii/Database_ENG.csv` — CSV copy for direct Python use and cross-checking.
- `data/raw/IACOFI_2023_STATA.zip` — original official Stata archive.
- `data/raw/IACOFI_2023_ASCII.zip` — original official ASCII archive.

Official downloads:

- [2023 Stata archive](https://www.bancaditalia.it/statistiche/tematiche/indagini-famiglie-imprese/alfabetizzazione/Database_STATA_EN.zip?language_id=1)
- [2023 ASCII archive](https://www.bancaditalia.it/statistiche/tematiche/indagini-famiglie-imprese/alfabetizzazione/Database_ASCII_EN.zip?language_id=1)

## Banca d'Italia documentation

- `documentation/banca_ditalia/IACOFI_2023_Data_Description.pdf` — English questionnaire, variable names, response codes and labels.  
  [Official PDF](https://www.bancaditalia.it/statistiche/tematiche/indagini-famiglie-imprese/alfabetizzazione/Data-description-2023.pdf?language_id=1)

- `documentation/banca_ditalia/Banca_dItalia_IACOFI_2023_Results_IT.pdf` — official Italian results and reference means for validating reconstructed scores.  
  [Official PDF](https://www.bancaditalia.it/pubblicazioni/indagini-alfabetizzazione/2023-indagini-alfabetizzazione/statistiche_AFA_20072023.pdf)

Published reference means:

- Traditional financial literacy: 10.7/20
- Digital financial literacy: 4.6/10
- Digital knowledge: 1.3/3
- Digital behaviour: 2.1/4
- Digital attitudes: 1.2/3

## OECD methodology and context

- `documentation/oecd/OECD_INFE_2022_Toolkit.pdf` — questionnaire methodology and the official scoring rules for traditional and digital financial literacy. Annex A is the main scoring reference.  
  [Official PDF](https://www.oecd.org/content/dam/oecd/en/publications/reports/2022/03/oecd-infe-toolkit-for-measuring-financial-literacy-and-financial-inclusion-2022_54dba970/cbc4114f-en.pdf)

- `documentation/oecd/OECD_INFE_2023_International_Survey.pdf` — international context and cross-country results for the survey round using the 2022 toolkit.  
  [Official PDF](https://www.oecd.org/content/dam/oecd/en/publications/reports/2023/12/oecd-infe-2023-international-survey-of-adult-financial-literacy_8ce94e2c/56003a32-en.pdf)

- `documentation/oecd/OECD_2025_Digital_Payments_and_DFL.pdf` — policy context on digital payments, online risks and digital financial literacy.  
  [Official PDF](https://www.oecd.org/content/dam/oecd/en/publications/reports/2025/09/supporting-informed-and-safe-use-of-digital-payments-through-digital-financial-literacy_5e6b71b3/21de47d1-en.pdf)

## Variables central to Project 2

Official digital financial literacy items:

- Knowledge: `qk7_4`, `qk7_5`, `qk7_6`
- Behaviour: `qs2_6`, `qs2_7`, `qs2_8`, `qs3_13`
- Attitudes: `qs4_1`, `qs4_2`, `qs4_3`

Additional variables available for later analysis include internet access (`qd14`), general digital activity (`qd6_*`), online financial activity (`qp8_*`, `qp9_*`), adverse experiences and scams (`qp10_*`), socio-demographic characteristics, and the survey weight (`wght`).


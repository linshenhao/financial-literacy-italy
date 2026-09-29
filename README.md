<div align="center">

# Traditional and Digital Financial Literacy in Italy

<p><strong>A reproducible study of financial skills, digital participation, and the information hidden by a single overall score.</strong></p>

<p>
  <img src="https://img.shields.io/badge/Python-Analysis-3776AB?logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/pandas-Data%20Analysis-150458?logo=pandas&logoColor=white" alt="pandas">
  <img src="https://img.shields.io/badge/SciPy-Statistics-8CAAE6?logo=scipy&logoColor=white" alt="SciPy">
  <img src="https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white" alt="Jupyter">
  <img src="https://img.shields.io/badge/Matplotlib-Visualization-11557C" alt="Matplotlib">
</p>

<p>
  <a href="https://github.com/linshenhao"><img src="https://img.shields.io/badge/GitHub-Stefano%20Lin-181717?logo=github&logoColor=white" alt="GitHub"></a>
  <a href="https://www.linkedin.com/in/linshenhao-49b127393"><img src="https://img.shields.io/badge/LinkedIn-Stefano%20Lin-0A66C2?logo=linkedin&logoColor=white" alt="LinkedIn"></a>
</p>

<p><strong>English</strong> | <a href="README.zh-CN.md">简体中文</a></p>

</div>

---

Should traditional and digital financial literacy be reported as one overall score, or as two separate measures? This Data Science Lab project explores that question using the 2023 Italian IACOFI survey from Banca d'Italia.

The analysis finds that the two dimensions are related, but they identify different groups of people. Reporting them separately, alongside their joint distribution, preserves information that a combined score could hide.

## Contents

- [1. Data](#1-data)
- [2. Research workflow](#2-research-workflow)
- [3. Results and interpretation](#3-results-and-interpretation)
- [4. Conclusion and limitations](#4-conclusion-and-limitations)
- [5. Repository structure](#5-repository-structure)
- [6. Getting started](#6-getting-started)
- [7. Sources and AI assistance](#7-sources-and-ai-assistance)
- [8. Author](#8-author)

---

## 1. Data

- **Source:** [Banca d'Italia — Financial literacy of Italian adults](https://www.bancaditalia.it/statistiche/tematiche/indagini-famiglie-imprese/alfabetizzazione/index.html?com.dotmarketing.htmlpage.language=1)
- **Survey:** IACOFI 2023
- **Full sample:** 4,862 Italian residents aged 18–79; 219 variables
- **Comparison sample:** 4,427 respondents with internet access
- **Weighting:** survey weights are used for reported means and percentages

Respondents without internet access are excluded from comparisons of the two scores because the digital module is conditional on internet access. They are not assigned a digital score of zero.

---

## 2. Research workflow

The notebook reconstructs traditional literacy (knowledge, behaviour, and attitudes; 0–20) and digital literacy (the same three components; 0–10), following OECD/INFE scoring rules. It checks the reconstructed means against the official results, converts both totals to a 0–100 scale, and examines:

1. The association between traditional and digital scores.
2. Four profiles defined using a 70% target.
3. Differences by age, gender, education, and region.
4. Digital financial activities, online products, and reported adverse financial experiences.

Python is used throughout, with pandas, NumPy, SciPy, Matplotlib, and Seaborn. The workflow is documented in [project2_analysis.ipynb](project2_analysis.ipynb).

---

## 3. Results and interpretation

### The scores overlap, but are not interchangeable

The reconstructed weighted means reproduce the published results after rounding: **10.7/20** for traditional literacy and **4.6/10** for digital literacy. Traditional means use the full sample; digital means use internet users.

Among internet users, the Spearman correlation between the two scores is **0.443**. People with similar traditional scores can have quite different digital scores.

<p align="center">
  <img src="output/figures/traditional_vs_digital.png" alt="Traditional versus digital financial literacy" width="80%">
</p>

<p align="center"><em>Figure 1. Scores among internet users. Dashed lines mark the 70% target.</em></p>

### More than a quarter meet only one target

| Profile | Weighted share of internet users |
|---|---:|
| Both meet target | 5.84% |
| Traditional only | 11.70% |
| Digital only | 14.37% |
| Neither meets target | 68.09% |

**26.07% meet exactly one target.** These mixed profiles are the main reason to keep the two dimensions visible: a combined score would not show which area needs attention.

<p align="center">
  <img src="output/figures/literacy_profiles.png" alt="Four literacy profiles" width="80%">
</p>

<p align="center"><em>Figure 2. Weighted profile shares. More than one quarter meet exactly one target.</em></p>

### Education shows the clearest demographic gap

On the 0–100 scale, respondents in the tertiary education group average **59.54** in traditional literacy and **51.42** in digital literacy. Those with lower secondary education or less average **48.03** and **40.64**. Gender and regional differences are smaller. Mixed profiles appear in every age and education group.

<p align="center">
  <img src="output/figures/demographic_scores.png" alt="Literacy scores by demographic group" width="100%">
</p>

<p align="center"><em>Figure 3. Weighted mean scores by gender, age, education, and region.</em></p>

### Digital participation and adverse experiences have different patterns

Respondents meeting both targets report an average of **4.23** digital financial activities and **0.86** products obtained online. Those meeting neither report **3.90** activities and **0.45** online products. The traditional-only and digital-only profiles have almost identical activity counts: **4.15** and **4.14**.

The share reporting at least one adverse financial experience ranges from **13.34% to 16.13%** across profiles. These descriptive results do not establish that higher literacy prevents harm. More frequent users may also have more opportunities to encounter problems.

<p align="center">
  <img src="output/figures/digital_activity_and_risk.png" alt="Digital financial activity and adverse experiences" width="100%">
</p>

<p align="center"><em>Figure 4. Digital participation and reported adverse experiences across the four profiles.</em></p>

---

## 4. Conclusion and limitations

The results support **reporting traditional and digital financial literacy separately, while presenting them together**. This can help education providers and public institutions distinguish weaknesses in everyday financial skills from weaknesses in digital financial skills.

The study is descriptive and specific to Italy in 2023. It does not establish causal relationships or test whether the same patterns hold in other countries. Behaviour and adverse experiences are self-reported; the 70% threshold simplifies continuous scores; and the digital comparison does not cover people without internet access. The current analysis does not include threshold sensitivity tests or multivariable adjustment.

---

## 5. Repository structure

```text
financial-literacy-italy/
├── project2_analysis.ipynb     # Analysis and saved outputs
├── output/
│   ├── figures/               # Five analysis figures
│   └── tables/                # Nine exported result tables
├── SOURCES.md                 # Official data and documentation links
├── README.md                  # English introduction
└── README.zh-CN.md            # Chinese introduction
```

The raw survey data, downloaded documents, and LaTeX report are held locally and are not included in this repository.

## 6. Getting started

Clone the repository:

```bash
git clone https://github.com/linshenhao/financial-literacy-italy.git
cd financial-literacy-italy
```

Download the [official Stata archive](https://www.bancaditalia.it/statistiche/tematiche/indagini-famiglie-imprese/alfabetizzazione/Database_STATA_EN.zip?language_id=1) and place the extracted `Database_ENG.dta` at `data/raw/stata/Database_ENG.dta`.

Install the analysis packages:

```bash
pip install jupyter pandas numpy scipy matplotlib seaborn
```

Open `project2_analysis.ipynb` from the project folder and select **Restart Kernel and Run All Cells**. The notebook reads `data/raw/stata/Database_ENG.dta` and saves its tables and figures under `output/`.

---

## 7. Sources and AI assistance

Data belong to Banca d'Italia. Scoring follows the [OECD/INFE 2022 toolkit](https://doi.org/10.1787/cbc4114f-en). See [SOURCES.md](SOURCES.md) for official downloads and references.

OpenAI Codex assisted with code drafting, debugging, documentation, and report preparation. AI assistance is disclosed in the report; the analysis and interpretations require author review before submission.

## 8. Author

| Author | Links |
|---|---|
|**Shen Hao Stefano Lin** | <a href="https://github.com/linshenhao"><img src="https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=white" alt="GitHub"></a> <a href="https://www.linkedin.com/in/linshenhao-49b127393"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?logo=linkedin&logoColor=white" alt="LinkedIn"></a>|

---

<div align="center">

<p><strong>Built as a reproducible study of traditional and digital financial literacy in Italy.</strong></p>

<p><a href="project2_analysis.ipynb">Explore the notebook</a> · <a href="SOURCES.md">View the data sources</a> · <a href="README.zh-CN.md">阅读中文版</a></p>

</div>

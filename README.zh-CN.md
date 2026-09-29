<div align="center">

# 意大利传统与数字金融素养研究

<p><strong>通过可复现的数据分析，研究金融能力、数字参与，以及单一总分可能隐藏的人群差异。</strong></p>

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

<p><a href="README.md">English</a> | <strong>简体中文</strong></p>

</div>

---

传统金融素养和数字金融素养应该合成一个总分，还是分别报告？这个 Data Science Lab 项目使用意大利央行（Banca d'Italia）的 IACOFI 2023 调查数据，研究这两个维度是否能够相互替代。

结果表明，两者存在联系，但会识别出不同的人群。因此，分别保留两个分数，并同时展示它们的组合情况，比只提供一个合并总分更有信息量。

## 目录

- [1. 数据来源](#1-数据来源)
- [2. 研究流程](#2-研究流程)
- [3. 结果与解释](#3-结果与解释)
- [4. 结论与局限](#4-结论与局限)
- [5. 仓库结构](#5-仓库结构)
- [6. 运行方法](#6-运行方法)
- [7. 资料与 AI 使用说明](#7-资料与-ai-使用说明)
- [8. 作者](#8-作者)

---

## 1. 数据来源

- **来源：** [意大利央行成年人金融素养调查](https://www.bancaditalia.it/statistiche/tematiche/indagini-famiglie-imprese/alfabetizzazione/index.html?com.dotmarketing.htmlpage.language=1)
- **调查年份：** 2023 年（IACOFI 2023）
- **完整样本：** 4,862 名 18–79 岁意大利居民，共 219 个变量
- **两个分数的比较样本：** 4,427 名有互联网接入的受访者
- **统计方式：** 平均分和比例使用调查权重计算

数字金融问卷以互联网接入为条件。因此，没有互联网接入的受访者不参与两个分数的比较，也没有被直接记为数字金融素养零分。

---

## 2. 研究流程

按照 OECD/INFE 的计分规则，项目重建了传统金融素养分数（知识、行为、态度，总分 0–20）和数字金融素养分数（同样三个组成部分，总分 0–10）。先与央行公布的结果核对，再将两个总分转换为 0–100 分，开展以下分析：

1. 比较传统与数字金融素养的相关性。
2. 根据 70% 的目标线划分四类人群。
3. 比较不同年龄、性别、教育程度和地区的结果。
4. 分析数字金融活动、在线办理产品和负面金融经历。

代码使用 Python，主要工具为 pandas、NumPy、SciPy、Matplotlib 和 Seaborn。完整过程见 [project2_analysis.ipynb](project2_analysis.ipynb)。

---

## 3. 结果与解释

### 两个分数相关，但不能互相替代

重建后的加权平均分，四舍五入后与官方公布结果一致：传统金融素养为 **10.7/20**，数字金融素养为 **4.6/10**。前者使用完整样本，后者使用有互联网接入的人群。

在有互联网接入的人群中，两个分数的 Spearman 相关系数为 **0.443**。传统金融分数相近的人，数字金融分数仍可能相差较大。

<p align="center">
  <img src="output/figures/traditional_vs_digital.png" alt="传统与数字金融素养分数比较" width="80%">
</p>

<p align="center"><em>图1：有互联网接入人群的分数分布，虚线表示70%的目标线。</em></p>

### 超过四分之一的人只在一个维度达标

| 人群类型 | 有互联网接入人群中的加权比例 |
|---|---:|
| 两项都达标 | 5.84% |
| 只有传统金融素养达标 | 11.70% |
| 只有数字金融素养达标 | 14.37% |
| 两项都未达标 | 68.09% |

**26.07% 的人只在一个维度达标。** 这正是分别报告两个分数的主要理由：合并总分无法直接显示一个人究竟在哪方面需要帮助。

<p align="center">
  <img src="output/figures/literacy_profiles.png" alt="四类金融素养人群" width="80%">
</p>

<p align="center"><em>图2：四类人群的加权比例，超过四分之一的人只在一个维度达标。</em></p>

### 教育程度的差异最明显

在 0–100 分制下，高等教育组的传统和数字金融平均分分别为 **59.54** 和 **51.42**；初中及以下教育组分别为 **48.03** 和 **40.64**。性别和地区之间的差异相对较小。每个年龄和教育组中，都存在只在一个维度达标的人。

<p align="center">
  <img src="output/figures/demographic_scores.png" alt="不同人口特征的金融素养平均分" width="100%">
</p>

<p align="center"><em>图3：按性别、年龄、教育程度和地区计算的加权平均分。</em></p>

### 数字金融参与和负面经历并不遵循同一种规律

两项都达标的人平均参与 **4.23** 种数字金融活动，在线办理 **0.86** 类金融产品；两项都未达标的人分别为 **3.90** 种活动和 **0.45** 类产品。只有传统达标和只有数字达标两组的活动数量非常接近，分别为 **4.15** 和 **4.14**。

四类人群中，至少报告一种负面金融经历的比例介于 **13.34%–16.13%**。这些描述性结果不能证明金融素养越高就越能避免损失，因为更频繁地使用数字服务，也可能意味着更多接触风险的机会。

<p align="center">
  <img src="output/figures/digital_activity_and_risk.png" alt="数字金融活动和负面经历" width="100%">
</p>

<p align="center"><em>图4：四类人群的数字金融参与和自报负面经历。</em></p>

---

## 4. 结论与局限

研究支持**分别报告传统和数字金融素养，同时展示它们的组合情况**。这样可以帮助教育机构和公共部门区分日常金融能力与数字金融能力上的不足。

本研究描述的是意大利 2023 年的情况，不能证明因果关系，也没有检验其他国家是否存在相同规律。行为和负面经历来自受访者自报；70% 的分界线简化了连续分数；数字比较没有覆盖无互联网接入者。目前尚未进行分界线敏感性分析或多变量调整。

---

## 5. 仓库结构

```text
financial-literacy-italy/
├── project2_analysis.ipynb     # 分析代码和已保存的结果
├── output/
│   ├── figures/               # 5张分析图表
│   └── tables/                # 9份结果表格
├── SOURCES.md                 # 官方数据和资料链接
├── README.md                  # 英文介绍
└── README.zh-CN.md            # 中文介绍
```

原始调查数据、下载的文献和 LaTeX 报告保存在本地，没有上传到这个仓库。

## 6. 运行方法

克隆仓库：

```bash
git clone https://github.com/linshenhao/financial-literacy-italy.git
cd financial-literacy-italy
```

下载[官方 Stata 数据压缩包](https://www.bancaditalia.it/statistiche/tematiche/indagini-famiglie-imprese/alfabetizzazione/Database_STATA_EN.zip?language_id=1)，将解压得到的 `Database_ENG.dta` 放到 `data/raw/stata/Database_ENG.dta`。

安装分析所需的 Python 包：

```bash
pip install jupyter pandas numpy scipy matplotlib seaborn
```

在项目文件夹中打开 `project2_analysis.ipynb`，选择 **Restart Kernel and Run All Cells**。Notebook 会读取 `data/raw/stata/Database_ENG.dta`，将表格和图片保存到 `output/`。

---

## 7. 资料与 AI 使用说明

数据来自意大利央行，计分方法依据 [OECD/INFE 2022 工具包](https://doi.org/10.1787/cbc4114f-en)。官方数据下载地址和参考资料见 [SOURCES.md](SOURCES.md)。

OpenAI Codex 协助了代码起草、调试、文档和报告整理。报告中已披露 AI 的使用；提交前仍需由作者核查分析和解释。

## 8. 作者

| 作者 | 链接 |
|---|---|
|**Shen Hao Stefano Lin** | <a href="https://github.com/linshenhao"><img src="https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=white" alt="GitHub"></a> <a href="https://www.linkedin.com/in/linshenhao-49b127393"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?logo=linkedin&logoColor=white" alt="LinkedIn"></a>|

---

<div align="center">

<p><strong>一个可复现的意大利传统与数字金融素养研究项目。</strong></p>

<p><a href="project2_analysis.ipynb">查看分析代码</a> · <a href="SOURCES.md">查看数据来源</a> · <a href="README.md">Read in English</a></p>

</div>

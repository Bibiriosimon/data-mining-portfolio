# 数据挖掘实战项目集

<div align="center">

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0+-orange.svg)](https://scikit-learn.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen.svg)](https://github.com/Bibiriosimon/data-mining-portfolio)

</div>

---


---

## 关于本仓库

本仓库汇集了数据挖掘课程的全部实战作业，覆盖从 **NumPy/Pandas 基础**到**分类、回归、聚类**的端到端机器学习流水线。每个项目以 Jupyter Notebook 呈现，包含完整代码、可视化输出与分析结论。

其中 **[天气预测](11_weather_prediction/)** 为独立研究课题——通过 Open-Meteo API 获取成都 5 年气象数据，构建 18 维时间序列特征，对比多元线性回归、CCP 剪枝决策树与 XGBoost 的性能差异，并基于特征重要性识别关键气象驱动因素。

> 所有数据集已脱敏，可直接运行复现。

---

## 项目目录

| # | 项目名称 | 算法 / 重点 | 业务场景 |
|---|---------|-------------|---------|
| 01 | [NumPy 基础](01_numpy_basics/) | 数组运算与线性代数 | 数值计算基础 |
| 02 | [Pandas 基础](02_pandas_basics/) | Series、DataFrame 操作 | 数据读取与清洗 |
| 03 | [数据可视化](03_data_visualization/) | 饼图、分类汇总、EDA | 房产数据探索 |
| 04 | [数据预处理](04_data_preprocessing/) | 等宽分箱、标准化 | 特征工程入门 |
| 05 | [信用卡欺诈检测](05_decision_tree_fraud/) | **决策树**、不平衡分类 | 金融风控 |
| 06 | [文本分类对比](06_naive_bayes_text/) | **MultinomialNB vs BernoulliNB** | 新闻主题识别 |
| 07 | [客户信用风险预测](07_credit_risk/) | **决策树 vs 朴素贝叶斯**、ROC/AUC | 银行信贷审批 |
| 08 | [学生心理健康筛查](08_svm_mental_health/) | **SVM**（线性/多项式/RBF）、GridSearchCV | 高校心理辅导 |
| 09 | [房价回归预测](09_house_price_regression/) | **线性回归、决策树回归** | 房地产估值 |
| 10 | [客户群体划分](10_customer_segmentation/) | **K-Means 聚类**、肘部法则 | 零售精准营销 |
| 11 | [天气预测](11_weather_prediction/) | **RandomForest、XGBoost**、时序特征工程 | 气象预报 |

---

## 技术栈

| 层级 | 工具 / 库 |
|------|----------|
| 数据处理 | NumPy · Pandas |
| 可视化 | Matplotlib · Seaborn |
| 机器学习 | scikit-learn（DecisionTree · NaiveBayes · SVM · RandomForest · KMeans · LinearRegression） |
| 文本特征 | CountVectorizer · TfidfVectorizer |
| 数据获取 | Open-Meteo API · CSV |

---

## 核心能力展示

- **端到端 ML 流水线** — 数据获取 → 清洗 → EDA → 特征工程 → 建模 → 评估 → 结论
- **监督学习** — 二分类与多分类、回归任务
- **无监督学习** — K-Means 聚类 + 手肘法 + 轮廓系数
- **模型评估** — 混淆矩阵、精确率/召回率/F1、ROC-AUC、交叉验证、GridSearchCV
- **特征工程** — 标准化（StandardScaler）、编码（OneHot/Label）、文本向量化、时间序列特征（滞后/滑动窗口/周期编码）
- **数据可视化** — 分布图、热力图、决策边界、ROC 曲线、决策树结构

---

## 快速开始

```bash
# 克隆仓库
git clone https://github.com/Bibiriosimon/data-mining-portfolio.git
cd data-mining-portfolio

# 安装依赖
pip install -r requirements.txt

# 启动 Jupyter
jupyter notebook
```

---

## 数据集说明

| 数据集 | 来源 | 样本量 | 特征数 |
|--------|------|--------|--------|
| creditcard.csv | 模拟信用卡交易记录 | 1,000 | 13 |
| MiniNews_TextSet.csv | 科技 vs 体育新闻短文本 | 60 | 文本 |
| credit_risk_data.csv | 模拟贷款申请人画像 | 300 | 8 |
| mental_health_survey.csv | 模拟学生心理健康问卷 | 800 | 9 |
| Supermarket-customers.csv | 零售客户购买行为 | 469 | 4 |
| chengdu_weather | Open-Meteo 历史数据 API（2019–2024） | 2,192 | 7 |

---

## 许可

MIT License — 欢迎 Star、Fork 与交流。

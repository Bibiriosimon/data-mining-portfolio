# 11 · 气温预测——成都逐日气温时序预测研究

本项目以成都地区 2019–2024 年逐日平均气温为研究对象，分两个阶段探索了不同建模范式下的气温预测方法。两个阶段使用的是同一份底层数据集，但在**如何理解和利用时间信息**这一核心问题上思路截然不同。

---

## 项目结构

```
11_weather_prediction/
├── part1_machine_learning/            # 第一阶段：机器学习方法（XGBoost、随机森林、决策树）
│   └── weather_prediction.ipynb
│
└── part2_time_series_deep_learning/   # 第二阶段：时间序列与深度学习（ARIMA、LSTM、TCN）
    ├── 01_data_preprocessing_arima.ipynb
    ├── 02_lstm_model.ipynb
    ├── 03_tcn_model.ipynb
    ├── 04_model_comparison.ipynb
    └── chengdu_weather_clean.csv
```

---

## 第一阶段 · 机器学习基线（`part1_machine_learning/`）

将每一天视为**独立样本**，通过手工构造多变量特征来训练经典机器学习模型。

| 项目 | 说明 |
|------|------|
| 模型 | 决策树、随机森林、XGBoost |
| 输入特征 | 最高气温、最低气温、降水量、风速、辐射量（多变量） |
| 核心假设 | 每天的观测值相互独立，不考虑时间顺序 |
| 评估方式 | 交叉验证 |
| 最优结果 | XGBoost：R²=0.894，RMSE=2.82°C，MAE=2.28°C |

---

## 第二阶段 · 时间序列与深度学习（`part2_time_series_deep_learning/`）

将数据视为有序的时间序列，通过构造历史滑动窗口来显式建模**时间依赖结构**。

| 项目 | 说明 |
|------|------|
| 模型 | ARIMA(3,1,2)、LSTM、TCN |
| 输入特征 | 仅使用平均气温（单变量），30 天滑动窗口 |
| 核心假设 | 今天的气温与近期历史密切相关，时间顺序至关重要 |
| 评估方式 | Walk-Forward 滚动预测（2024 年全年 366 天） |
| 最优结果（单步） | ARIMA：MAE=0.9859°C，R²=0.9753 |
| 最优结果（7步） | LSTM：MAE=2.4941°C |

### Notebook 运行顺序：
1. `01_data_preprocessing_arima.ipynb` — 数据清洗、异常值处理、ARIMA 建模
2. `02_lstm_model.ipynb` — LSTM 建模（含 Optuna 超参数优化）
3. `03_tcn_model.ipynb` — TCN 建模（含 Optuna 超参数优化）
4. `04_model_comparison.ipynb` — 三模型三组实验综合对比

---

## 核心结论

> 不存在普遍最优的预测模型，最佳方法取决于**实际预测步长需求**：
> - **单步预测**场景下，ARIMA 的简洁线性结构与日均气温的短期自相关特性高度契合，表现最优
> - **多步预测（H≥2）**场景下，LSTM 的门控记忆机制优势随步长增大逐渐显现，综合性能最佳
> - 第二阶段相比第一阶段，单步预测 MAE 从 XGBoost 的约 2.28°C 大幅提升至 **LSTM 的 0.99°C**，印证了显式建模时序结构的价值

---

## 数据来源

Open-Meteo 开放气象服务 · 成都（北纬 30.57°，东经 104.07°）· 2019-01-01 至 2024-12-31

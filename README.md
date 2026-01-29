
# nlp-disaster-tweet-classifier  
# 灾难推文分类器：基于 BERT 微调的内容安全风控实践

[![Kaggle](https://img.shields.io/badge/Kaggle-NLP%20Getting%20Started-20BEFF?logo=kaggle)](https://www.kaggle.com/c/nlp-getting-started)
[![License](https://img.shields.io/badge/License-MIT-blue)](LICENSE)

This project implements a solution for the Kaggle competition **[Natural Language Processing with Disaster Tweets](https://www.kaggle.com/c/nlp-getting-started)**, aiming to accurately classify whether a social media tweet reports a real disaster (e.g., earthquake, explosion, flood) or not.  
不同于普通文本分类，本项目从**在线内容安全（Content Safety）与风控（Risk Control）** 的实战视角出发，将模型输出设计为可直接接入工业级风险评分系统的连续型信号，具备明确的业务集成价值。

## 🔍 Why This Project Matters / 为什么这个项目值得做？

In real-world risk control scenarios, simple keyword matching is easily bypassed by malicious actors (e.g., “🔥This fire is lit!🔥” vs “🔥Factory exploded in flames!🔥”). This solution addresses this by:
- 在真实风控场景中，仅靠关键词匹配极易被黑产绕过（例如：“🔥这火🔥烧得真旺” vs “🔥工厂爆炸起火🔥”）。本方案通过：
  - Leveraging **BERT’s deep semantic understanding** to capture contextual intent.
    - 利用 **BERT 的深层语义理解能力**，精准捕捉上下文意图；
  - Performing **full Supervised Fine-Tuning (SFT)** on `bert-base-uncased` for optimal performance.
    - 对 `bert-base-uncased` 进行**完整的监督式微调（SFT）**，以获得最佳性能；
  - Outputting a continuous **`text_risk_score` (disaster probability)**, enabling seamless integration with downstream rule engines or user risk profiling systems.
    - 输出连续型 **`text_risk_score`（灾难概率）**，便于与下游规则引擎或用户画像系统融合。

This capability can be directly applied to:
该能力可直接应用于：
✅ Real-time detection of false disaster information  
✅ 虚假灾难信息识别  
✅ High-risk content interception  
✅ 高危内容实时拦截  
✅ Anomalous account behavior modeling (e.g., mass-posting disaster rumors)  
✅ 账号异常行为建模（如批量发布灾难谣言）

## 📊 Results / 实验结果

| Metric / 指标 | Value / 数值 |
|---------------|--------------|
| Kaggle Public Score | **0.83205** |
| Validation F1-Score (Macro) | **0.8461** |
| Training Epochs | 2 |

> The model demonstrates strong generalization, effectively distinguishing between literal disasters and figurative uses (e.g., "This traffic is a disaster!").  
> 模型展现出良好的泛化能力，能有效区分“灾难隐喻”（如 "This traffic is a disaster!"）与真实事件。

## 🗂️ Repository Structure / 仓库结构


> 💡 The notebook includes detailed comments covering text preprocessing, tokenizer configuration, dataset construction, and risk feature generation logic.  
> 💡 Notebook 中包含详细注释，涵盖文本预处理、Tokenizer 配置、数据集构建及风险特征生成逻辑。

## ▶️ How to Run Locally / 如何本地运行？

### 1. Get the Data / 获取数据
Visit the [Kaggle competition page](https://www.kaggle.com/c/nlp-getting-started/data), log in, accept the rules, and download:
- `train.csv`
- `test.csv`
- `sample_submission.csv`

Place them in your project root directory.

### 2. Set Up Environment / 配置环境

pip install -r requirements.txt
jupyter notebook kaggle_nlp-getting-started-0129.ipynb


## ⚠️ Data & Compliance Notice / 数据与合规说明

> **This repository does NOT and WILL NOT include any original Kaggle data files (e.g., `train.csv`, `test.csv`).**

- **Data Source**: All data used is from the official Kaggle competition **[Natural Language Processing with Disaster Tweets](https://www.kaggle.com/c/nlp-getting-started)**.
- **授权范围 / License Scope**: Per competition rules, the dataset is for **“Competition Use and Academic, Non-Commercial Use Only”**. See [Official Rules](https://www.kaggle.com/competitions/nlp-getting-started/rules).
- **明确禁止 / Explicitly Prohibited**: Rule 7.B states: **“You may not transmit, copy, publish, or otherwise provide the Competition Data to any non-participant third party.”**
- **我的承诺 / My Commitment**:  
  **I strictly comply with these terms. No original data has been distributed in any form. This repository contains only my independently developed code, analysis, and model implementation.**

> 📌 **To Technical Interviewers**: In roles like Content Safety, Anti-Fraud, and Risk Control, **data compliance awareness is as critical as engineering skill**. The structure of this project reflects my deep understanding of IP, platform rules, and responsible AI development — not just a legal baseline, but a core tenet of professional engineering.
>
> 📌 **致技术面试官**：在内容安全、反欺诈、风控等岗位中，**数据合规意识与工程能力同等重要**。此项目的结构设计体现了我对知识产权、平台规则及负责任 AI 开发的深刻理解——这不仅是法律底线，更是专业工程师的核心素养。


# Disaster Tweet Classifier  
### 基于微调 BERT 的灾难推文识别系统（内容安全风控实践）

[![Kaggle](https://img.shields.io/badge/Kaggle-NLP%20Getting%20Started-20BEFF?logo=kaggle)](https://www.kaggle.com/c/nlp-getting-started)  
[![License](https://img.shields.io/badge/License-MIT-blue)](LICENSE)

本项目基于 Kaggle 官方竞赛 [Natural Language Processing with Disaster Tweets](https://www.kaggle.com/c/nlp-getting-started)，通过微调 BERT 模型，实现对社交媒体文本中**真实灾难事件**（如地震、爆炸、火灾）的高精度识别，服务于内容安全与账号风险控制场景。

---

## 🔍 项目价值

在实际内容审核中，关键词规则极易被绕过（例如：“🔥这火🔥烧得真旺” vs “🔥工厂爆炸起火🔥”）。本方案通过以下方式提升系统鲁棒性：

- **语义理解（Semantic Understanding）**：利用 BERT 的上下文建模能力，准确捕捉文本真实意图；
- **可集成输出（Production-ready Output）**：输出连续型风险分 `text_risk_score`（即灾难概率），可直接接入风控规则引擎或用户画像系统；
- **高效训练（Efficient Tuning）**：在单卡 GPU 上对 `bert-base-uncased` 进行全参数微调，仅需 2 个 epoch 即达到验证 F1 0.85，支持策略高频迭代。

**适用场景**：
- 实时高危内容过滤
- 虚假/谣言信息识别
- 异常账号行为检测（如批量发布灾难类谣言）

---

## 📊 实验结果

| Metric                     | Score     |
|---------------------------|-----------|
| Kaggle Public LB Score    | **0.8446** |
| Validation F1-Score (Macro) | **0.8496** |
| Training Epochs           | 2         |

> 模型能有效区分“灾难隐喻”（如 *“This traffic is a disaster!”*）与真实事件，具备良好泛化能力。

---

## 🗂️ 项目结构

kaggle_nlp-getting-started-20260130.ipynb # 主训练与推理脚本
requirements.txt # 依赖清单
README.md # 项目说明
LICENSE # MIT 开源协议


> Notebook 包含完整的文本清洗、数据划分、模型训练、评估及提交逻辑，代码结构清晰，符合工程规范。

---

## ▶️ 本地运行

### 1. 获取数据
前往 [Kaggle 竞赛页面](https://www.kaggle.com/c/nlp-getting-started/data)，登录后下载以下文件，并置于项目根目录：
- `train.csv`
- `test.csv`
- `sample_submission.csv`

### 2. 配置环境

```bash
pip install -r requirements.txt
```

> 推荐使用 Python 3.9+ 虚拟环境以避免依赖冲突。



### 3. 运行训练与推理
在 Jupyter Notebook 中打开 `kaggle_nlp-getting-started-20260130.ipynb`，按顺序执行所有单元格，最终将生成 `submission.csv` 用于 Kaggle 提交。

---

## ⚠️ 数据合规声明

> **本仓库不包含任何原始 Kaggle 数据文件。**

- **数据来源**：Kaggle 官方竞赛 [Natural Language Processing with Disaster Tweets](https://www.kaggle.com/c/nlp-getting-started)  
- **使用范围**：严格遵循竞赛规则，仅用于 **竞赛及学术非商业用途**  
- **我的承诺**：未分发、未修改、未商用任何原始数据，本仓库仅包含自主编写的代码与模型逻辑

> 📌 **致招聘方**：在内容安全与风控岗位，**数据合规意识与工程能力同等重要**。本项目的设计体现了我对平台规则、知识产权及负责任 AI 开发的理解——这不仅是合规底线，更是专业工程师的基本素养。



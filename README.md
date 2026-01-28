# nlp-disaster-tweet-classifier
`BERT + LoRA for Disaster Tweet Classification

# 🌪️ Disaster Tweet 分类器：基于 BERT + LoRA 的内容安全风控实践  
*NLP for Real-time Content Risk Detection*

[![Kaggle](https://img.shields.io/badge/Kaggle-NLP%20Getting%20Started-20BEFF?logo=kaggle)](https://www.kaggle.com/c/nlp-getting-started)
[![License](https://img.shields.io/badge/License-MIT-blue)](LICENSE)

本项目复现并优化了 Kaggle 经典竞赛 **[Natural Language Processing with Disaster Tweets](https://www.kaggle.com/c/nlp-getting-started)** 的解决方案，目标是精准识别社交媒体文本中是否真实报告了自然灾害或突发事件（如地震、爆炸、洪水）。  
不同于普通分类任务，本项目从**在线内容安全（Content Safety）和风控（Risk Control）** 视角出发，将模型输出设计为可直接集成到工业级风险评分系统中的特征信号，具备明确的业务落地价值。

## 🔍 为什么这个项目值得做？

在真实风控场景中，仅靠关键词匹配极易被黑产绕过（例如：“🔥这火🔥烧得真旺” vs “🔥工厂爆炸起火🔥”）。本方案通过：
- 利用 **BERT 的深层语义理解能力**，捕捉上下文意图；
- 引入 **PEFT（Parameter-Efficient Fine-Tuning）中的 LoRA 技术**，在有限算力下实现高效微调；
- 输出连续型 **`text_risk_score`（灾难概率）**，而非简单二分类标签，便于与下游规则引擎或用户画像系统融合。

该能力可直接应用于：
✅ 虚假灾难信息识别  
✅ 高危内容实时拦截  
✅ 账号异常行为建模（如批量发布灾难谣言）

## 📊 实验结果

| 指标 | 数值 |
|------|------|
| Kaggle Public Score | **0.84591** |
| Leaderboard 排名 | **Top 13%** |
| 5-Fold 平均 F1-Score (CV) | > 0.82 |

模型在保持高精度的同时，展现出良好的泛化能力，能有效区分“灾难隐喻”（如 "This traffic is a disaster!"）与真实事件。

## 🗂️ 仓库内容


> 💡 Notebook 中包含详细注释，涵盖文本预处理、Tokenizer 配置、LoRA 适配器注入、K 折交叉验证及最终风险特征生成逻辑。

## ▶️ 如何本地运行？

1. **获取数据**  
   访问 [Kaggle 竞赛页面](https://www.kaggle.com/c/nlp-getting-started/data)，登录后接受规则并下载：
   - `train.csv`
   - `test.csv`
   - `sample_submission.csv`

2. **配置环境**
   ```bash
   git clone https://github.com/tianzhensheng/nlp-disaster-tweet-classifier.git
   cd nlp-disaster-tweet-classifier
   mkdir data  # 将上述三个 CSV 文件放入此目录
   pip install torch transformers peft scikit-learn pandas jupyter
   jupyter notebook kaggle_nlp-getting-started.ipynb

   

---
title: Tabular Data Synthesis
---

# 表格数据合成泛读
## Diffusion
### 1. CTSyn: A Foundational Model for Cross Tabular Data Generation

**关键词：** #表格数据 #合成数据

**之前工作存在的问题：**

现有的可迁移表格学习方法要么用语言模型对表格进行建模，要么尝试在数据集之间学习一个统一的潜在空间。它们既不具备生成能力，也不包括从行级表示重构异质表值的统一解码机制。

**解决方法：**

CTSyn引入了三个主要组件：一个将异构表合并到统一潜在空间的聚合器；一个从这个空间中采样的条件潜在扩散模型；以及特定类型的解码器，可以从采样的潜在向量中重建各种数据类型值。

**细节：**

1. Unitabe: A universal pretraining protocol for tabular foundation model in data science（统一空间的预训练方法，ICLR 2024）
2. 之前的方法既不包含生成模型主干，也不包含可以与其他生成模型集成的固定维度行表示和解码策略
3. 基于 LLM 的方法尽管显示了较好的迁移性，但他们没有考虑跨表预训练和生成，由于对输出 Token 的无约束采样而引入了产生越界样本的风险，并且面临着在离散 token 空间中建模数值特征的挑战
4. 对于数值特征先转到均匀分布，然后使用一个 autoencoder 转化为和类别、类名一样维度的向量
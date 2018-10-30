# BERT

## 1、简介

​	BERT 的全称是基于 Transformer 的双向编码器表征，其中「双向」表示模型在处理某一个词时，它能同时利用前面的词和后面的词两部分信息。这种「双向」的来源在于 BERT 与传统语言模型不同，它不是在给定所有前面词的条件下预测最可能的当前词，而是随机遮掩一些词，并利用所有没被遮掩的词进行预测。下图展示了三种预训练模型，其中 BERT 和 ELMo 都使用双向信息，OpenAI GPT 使用单向信息。

如上所示为不同预训练模型的架构，BERT 可以视为结合了 OpenAI GPT 和 ELMo 优势的新模型。其中 ELMo 使用两条独立训练的 LSTM 获取双向信息，而 OpenAI GPT 使用新型的 Transformer 和经典语言模型只能获取单向信息。BERT 的主要目标即在 OpenAI GPT 的基础上对预训练任务做一些改进，以同时利用 Transformer 深度模型与双向信息的优势。

BERT 的核心过程非常简洁，它会先从数据集抽取两个句子，其中第二句是第一句的下一句概率是 50%，这样就能学习句子之间的关系。其次随机去除两个句子中的一些词，并要求模型预测这些词是什么，这样就能学习句子内部的关系。最后再将经处理的句子传入大型 Transformer 模型，并通过两个损失函数同时学习上面两个目标就能完成训练。

## 2、算法流程

## 3、算法实现

目前网上的几个实现：

https://github.com/brightmart/bert_language_understanding

这个项目是对《BERT：Pre-training of Deep Bidirectional Transformers for Language Understanding》和《Attention is all You Need》这两篇论文的 tensorflow 实现。

我读完这两篇论文的主要感受以及存在的问题：


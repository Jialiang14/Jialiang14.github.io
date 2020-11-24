---
layout: post
title: 病理学研究进展
category: 生活
tags: Essay
keywords: 生活,2020
description: 论文
---


## 论文英语句子笔记
## Deep neural network models for computational histopathology: A survey  

组织病理学图像包含丰富的表型信息，可用于监测促成疾病进展和患者生存结果的潜在机制。近年来，深度学习已成为分析和解释组织学图像的主流方法论选择。在本文中，我们对组织病理学图像分析中使用的最新深度学习方法进行了全面回顾。通过对130余篇论文的调查，我们基于不同机器学习策略的方法论方面（如监督，弱监督，无监督，转移学习和这些方法的其他子变量）回顾了该领域的进展。我们还概述了适用于特定疾病的预后任务的基于深度学习的生存模型。最后，我们总结了几个现有的开放数据集，并重点介绍了当前深度学习方法的关键挑战和局限性，以及未来研究的可能途径。

## WSISA: Making Survival Prediction from Whole Slide Histopathological Images  （2017，CVPR）

基于图像的精密医学技术能够很好地用于治疗癌症病人。然而，完整地切片病理图像（WSI）像素值巨大，这使得不可能用传统的生存模型计算。这些模型通常采用来自感兴趣区域的手动标记来区分patches，并且无法直接从WSI中学习区分性补丁。作者认为由于癌症的异质性，仅使用一些小图无法完全表示患者的生存状态。另一个挑战是，生存预测通常没有足够的训练患者样本。为了克服这些挑战，作者通过自适应采样从每个WSI图像中提取数百个小图，然后将他们聚类成不同的组别。然后训练一个聚集模型，以基于簇级别的深度卷积生存预测结果进行患者级别的预测。这与现有的直接从WSI的部分区域提取的小图中提取特征的SOTA方法不同，提出的框架能够有效的开发和利用在WSI中所有的判别模式来预测患者的生存状态。

作者提出的方法不同于基于需要大量手工标注的图像的生存预测方法，他们提出的框架能够之间从WSI中提取多种模式。

由于以下原因，生存预测比是否有癌症的分类更具挑战性：

+ 生存预测是一个回归问题，患者的预测值排名很重要[20]。但在癌症分类任务中，预测结果分类是相互之间独立的
+ 在生存分析中，一个病人提供的不同WSI的信息应该聚集。然而，在文献[8]中，相同病人提供的WSI图像并没有被成功的汇总。
+ 在生存分析中，仅由病人提供真实标签（生存时间和身体状态）。WSI和Patch级别的真实标签是不知道的。当没有足够的数据训练CNN时，生存预测问题是很难的。

生存问题分类两个级别？patch-wise prediciton 和 patient-wise prediction。

#### 背景

生存分析的目的是预测事件发生之前的持续时间，并且感兴趣的事件是我们研究中癌症患者的死亡。

最近的癌症数据集（如TCGA）是长时间从病人的电子病历记录中收集的。*这使得在分析时，需要将时间维度的信息也考虑进去*。

正如文献[29]提到的，癌症微环境是一个复杂的环境，其中不仅包括癌细胞，还包括基质细胞和免疫细胞。这些“额外”的基因信息会影响结果，从而使从分子分析来诊断癌症成为一个有挑战的任务。最近的工作[25，27，28]尝试从图像角度解决该问题。

#### 方法

现有的生存分析方法大多集中在提取patch的局部信息，很少有工作处理WSI数据。

作者的方法分成四步：

+ 1、从WSI图像中自适应的采集patch；随机从WSI中选择patch，并假设这些patch能够捕获主要模式和属性。同一个病人的不同patch共同反应病人的生存情况。patch size 512*512
+ 2、根据patch的表型进行聚类分析；生成50x50的小图，共有2500维，使用pca降至50维，然后使用k-mean算法聚类。
+ 3、选择基于patch-wise的组进行生存分析预测性能；假定每个patch的生存标签来自病人，即一个病人有病，那么所有的patch都认为是有病？然后选择准确率比随机猜高一点的类作为在汇总过程中基本的学习者。
+ 4、汇总结果并租出最终的预测。此步是作者与其他方法拉开差距的关键。我们展示了如何统一来自一位患者的各种patch。病人总的patch数是他SWI中提取的所有patch数。为了估计每个模式的权重，我们需要统计每个聚类中patch的个数。因为在每个选择的cluster中，每个病人的patch数是不一样的，故各个权重也会不一样。

#### 实验

手工提取特征CellProfiler作为SOTA医学图像特征提取和定量分析工具。

作者在汇总时候采取了不同的方法？然后和传统的方法相比？

聚成10类。

汇总风险有两个好处：1）如果具有组织病理学图像的数据集中的样本量小得多，则训练样本少的高维特征将不适合一个好的预测模型。 输出风险的维度等于所选集群的数量，该数量远小于训练数据的大小； 2）一个集群的输出加权风险可以部分估计患者的存活率。

1. healthcare research   卫生保健研究
2. in the context of know 在已知的情况下
3. demands large volume of samples 需要大量的样本
4. censor 审查
5. molecular profiling data    分子谱数据（高维，所以需要特征选择，方法有[23,2,1,24,16,3]）
6. a complex milieu 复杂的环境
7. stromal cell 基质细胞
8. muddle   混乱的
9. phenotypes   表型
10. holistic 整体的
11. vice versa 反之则不是

## Development and validation of a deep learning algorithm for improving Gleason scoring of prostate cancer  (2019,nature)
#### 摘要

对于前列腺癌的病人，格里森评分是最重要的预后因素之一，可能独立于分期确定治疗方案。然而，格里森评分基于肿瘤形态的主观显微镜检查，并且再现性差。作者提出了一个深度学习系统，用于对前列腺全切片图像的格里森评分。该系统在1226个切片提取的112万病理学标注图像块上训练，使用331个切片作为独立的验证集。实验结果表明，作者的系统能达到70%的准确率，比病理学专家的61的准确率要高。与临床随访数据的相关性倾向于更好的患者风险分层。

#### Introduction

尽管Gleason在预测和病理管理方面具有无可争辩的角色，有病理学家进行格里森评分是一个主观的实践并且观察者间和观察者内变异性欠佳，有报道指出格里森评分在30%-53%之间波动[6-14].提高格里森评分的一致性和准确性的一个方法在于人工智能，其在已经在很多方面都有应用。当前用于格里森评分的主要是特征工程方法[30-32]，并且逐渐有人使用深度学习解决该问题，临床样本的二分类[26,33]，组织子区域的格里森评分[34,35]和微阵列[27,36],这些方法包括仔细选择癌症样本的子区域用于研究，在常规临床工作流程之外。

### 结果

性能指标包括：AUC，Cox models, C-index

作者表示，提出的系统可以作为决策支持工具。并且认为未来的研究需要评估在病人预测和相关性治疗决策时使用这些预测格里森评分方法对临床医学的影响。作者进一步探索了DLS在格里森评分中每一步以及他们各自的得分变异性。格里森评分的第一方面是对整个切片的区域级格里森模式分类。在这一步中，3维组织结构的2维组织学检查导致内在的模糊性。将离散分类应用于连续光谱上的腺体分化会产生较大的额外变异性，如在在小腺体和腺泡结构定义不明确之间格里森模式3、4之间的转换，或在融合腺体与巢或索之间的格里森模式4/5过渡。在区域级别分类后，格里森评分的下一步涉及对每个格里森模式的相对数量进行可视化，以确定最流行的模式。

作者认为其提出的“hard-negative mining”方法也能用于开发其他病理学深度学习算法。该算法的目的在于通过在整个数据集上使用推断来孤立出难以分类的样本并且进一步用这些样本去训练网络，从而提高算法的性能

#### 方法

作者使用了Inception-V3图像分类的网络结构，每层很少的卷积核，并且修改成FC层来提高全切片图像的推断结果。为了避免网格伪影，使用VALID替代SAME padding，并且裁剪了inception中的分支。网络的输入是911x911大小块的图像，网络评估的区域是每个图像块中心的32x32大小的区域。为了提高泛化性能，还是用了数据增强技术（饱和，对比度，亮度，hue，方向等）。在微调网络参数时，hard negative mini 和 ensembling被用于进一步提高网络的性能。在网络收敛后，使用了3个层面的集成技术：第一，使用0.9999参数的指数滑动均值对网络权重进行平滑。第二，对于每个图像块，模型的预测结果由8个图像方向构成，然后以几何均值的方法平均。第三，这些方向平均的预测被再次输入独立训练的模型（单独的hard-negative mining过程），然后再次使用几何均值。

#### 单词

1. stratifies  分层
2. prognostication  预测
3. microarrays  微阵列
4. comprise   包括
5. outside of routine clinical workflow.  在常规临床工作流程之外
6. genitourinary   泌尿生殖
7. granular  粒状
8. discordant  不和谐的
9. histologic examination   组织学检查

##  Computer aided quantification of intratumoral stroma yields an independent prognosticator in rectal cancer  (2019,Cellular)



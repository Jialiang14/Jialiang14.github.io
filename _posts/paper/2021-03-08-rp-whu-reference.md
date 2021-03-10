---
layout: post 
title: 博士研究计划参考文献阅读（武大）
category: 文献阅读
tags: paper reading
keywords: 医学实体命名识别、医学实体标准化、医学实体关系抽取
---

#### Artificial intelligence as the next step towards precision pathology （SCI 2区，2020）人工智能是精密病理学的下一步

##### 摘要

病理学是癌症护理的基石。随着个性化癌症治疗需要准确生物标志物评估，对癌症的组织病理学诊断中的准确率的需要正在增加。数字图像分析的出现有望改善组织形态学评估的数量和准确性。最近，机器学习，特别是深度学习促进了计算病理学的快速发展。将深度学习整合到日常护理将是下一个十年的护理领域的基石，组织病理学是是这场变革的中心。在病理学中，潜在高价值机器学习应用的例子包括基于日常诊断特征的模型评估和新特征提取和识别的能力，该新特征有望为疾病提供一个新的视角。最近的突破结果证明了在病理学中，机器学习应用方法极大提高了淋巴结点中癌症专辑检测效果，乳腺癌中ki67评分，腺癌中Gleason分级和黑色素瘤的肿瘤浸润淋巴细胞（TIL）评分。进一步地，基于深度学习模型已经被证明能够预测标准HE切片的肺、腺、胃和小分子癌症的小分子标志物的状态。此外，在很多疾病中如肺癌、小分子和胃癌，基于HE切片的预后（生存结果）深度神经网络模型已经证明了有效性。在本篇综述中，作者旨在提出和总结在数字图像分析和诊断病理学人工之恶能的最近进展。

##### 正文

可以在不损害生物标志物表达图像分析的情况下，对大型数字化的完整载玻片进行主要压缩和缩放[69]。作者分别介绍了深度学校在各种常见癌症诊断中的最新研究进展。

##### 限制和未来方向

尽管在很多任务中AI目前的记过显示出其能与人类专家性能相匹配的令人信服的结果，AI仍然存在限制和一些挑战。构成深度学习算法临床应用障碍的主要问题之一是解释和理解复杂AI模型如何做出决策有关的挑战，有时也被称为“黑盒”问题。可解释性AI盒可解释性机器学习方法是目前非常活跃的研究领域，提供深度学习模型不同层度的可解释性解决方案真在出现，可解释性问题在将来可能会减轻，至少部分是这样。建立可解释性机器学习方法对于临床实践而言非常关键，这将会解决一些医学社区常见的批评。另一方面，一旦AI满足所有临床使用，医学参与者同样需要接受一些这种限制。最近的研究表明，当仅用少量数据集进行训练时，目前的AI模型在独立数据集测试阶段将会出现20%的性能下降。

训练数据集的表示误差，如疾病的形态学差异等。关于技术差异的挑战可以通过标准化或严格控制处理，预处理图像数据来减少技术差异的影响，或者通过使模型对技术差异更加鲁棒来解决。在大量且多样数据集中训练或者fine-tuning深度学习模型有望减少泛化误差。

任何新测试的临床实践的应用都将由规则指导。对于新的AI工具，在CE-IVD认证下非常重要，它可以避免与特定实验室机器学习方法的潜在不可复现的风险。定义AI模型必须达到的最低性能水平，以使病理学家们能够接受使用它们是一个尚未解决的问题。（ defining the minimal level of performance that AI models would have to achieve for pathologists to accept using them is an issue that has not been addressed yet.）

##### 结论

随着个性化癌症治疗需求的增加，我们面临对更加准确生物标志物评估盒更加定量的组织病理学诊断来治疗并且提供高治理决策的迫切需求。病理学家需要配备新的方法论和工具，以提供所需的诊断敏感性和特异性，现在看来，人工智能是迈向精确病理学的下一步。

##### 词汇

1. cancer care 癌症护理
2. histopathologic  组织病理学
3. histomorphological 组织形态学
4. holds promise to 有望， be excepted to 
5. tumour-infiltrating lymphocyte (TIL) 肿瘤浸润淋巴细胞
6. gastric   胃的
7. prognostic  预后的
8. anatomic pathology  解剖病理学
9. stromal tissues 基质组织
10. be bound to 必然、必定
11. reproducibility 再现性、重复能力
12. controversy 争论、辩论
13. proliferation 增殖，分芽繁殖
14. active contour models 主动轮廓模型
15. high-through-put 高通量
16. assay 化验，分析试验，试样，试料
17. equivocal 模棱两可的，意义不明的，模糊的
18. inter-observer 观察员之间
19. intra-observer 观察者内部
20. profile 侧面，轮廓，外形，剖面
21. technical variability 技术差异
22. stratify 分层

#### ImageNet Large Scale Visual Recognition Challenge. (2015) ImageNet大规模视觉识别挑战赛（是介绍ImageNet数据集以及其中相应技术）

##### 摘要

ImageNet大规模视觉识别挑战赛是对数百种物体类别和数百万张图像进行物体类别分类和检测的基准。从2010年至今，每年都要进行一次挑战，吸引了50多个机构的参与。

本文描述了该基准数据集的创建以及由此带来的对象识别方面的进步。讨论了收集大规模真实标注数据的挑战，指出了在类别物体识别中的关键突破，提供了当前大规模数据分类和物体检测领域详细分析，并且用人类标准比较了最先进计算机视觉的识别准确率。最后以挑战赛的5年中获得的经验教训作为结束语，并提出未来的方向和改进建议。

#### An End-to-End Deep Learning Histochemical Scoring System for Breast Cancer TMA  (2018， Transaction on medical imaging, TMI, SCI 1区，医学顶刊) 一个乳腺癌TMA的端到端深度学习组织化学评分系统

##### 摘要

用于对乳腺癌的不同分子类别进行分层的方法之一是诺丁汉预后指数plus， 该指数使用与乳腺癌相关的生物标志物对组织微阵列上制备的肿癌组织进行染色。为了决定肿瘤的分子类别，病理学家们不得不通过显微镜对核活性生物标志物进行手工标记，并且使用一个半定量评估方法对每个TMA核心指定一个组织化学得分（H-Score)。手工标记正染色核是一项耗时，不精确，主观过程，这将会导致观察者间与观察者内差异。在本文，作者提出了一个端到端的深度学习系统，它可以直接自动地预测H-Score。系统模仿了病理学家决策过程，并且使用一个全卷积网络（FCN）来提取肿瘤核区域；一个多列卷积神经网络接收前两个FCN的输出和染色强度描述图像作为输入，作为一个高层决策制定机制来直接输出输入TMA图像的H-Score。就目前而言，该系统是一个使用TMA图像作为输入，并且直接输出临床得分的端到端系统。实验结果证明了使用作者提出的模型能以很高的、与病理学家评分具显著的统计相关性来预测H-Score，提出算法和病理学家之间H-Score的差异与病理学家之间的主观差异相当。

##### 正文

乳腺癌是一组具有不同基因型和表型特征的异质性肿瘤。最近基因表达谱的研究表明乳腺癌可以分成不同的分子肿瘤组。个性化BC管理通常使用鲁棒常用的技术，如针对肿瘤分子谱的免疫组织化学（IHC，免疫组化）。为了分类正染色像素和它们的强度，如颜色反卷积的方法在RGB图像中运用数学转换，这些方法被广泛地应用于从负染色中分离出正染色。

对于病理学家和CAD系统而言，传统评估方法至少有3个未解决的问题。首先，正染色强度需要分类成四个类别：未染色、弱、中性和强。然而，分类DAB染色强度尚未有标准定量准则。第一，两个病理学家通常将相同的染色强度分类成两个不同的类别或者将两个不同的强度分类成相同的强度。此外，人类视觉系统可能更多地关注强染色区域，但是这些强染色区域通常围绕着多种染色强度，这将会影响评估结果。第二，在评估中，细胞/核实例计数是一个非常重要的参数。尽管如此，人类和计算机仍然无法很好处理重叠细胞计数的困难。此外，不同核类型的外表的多样性，异质染色和复杂组织结构使得独立分割细胞/核成为一个非常有挑战的问题。第三，肿瘤核和正常核之间外表尺寸的差异将会影响肿瘤核评估的定量判断。在本文，作者想回答这样一个问题：开发一个像有经验的病理学家给出H-Score一样，直接对一个数字病理学图像给出高层评估的CAD模型是否可能？作者的创新在于模仿病理学家做出H-Score的过程，但是却不需要统计几种核的数量。

##### 方法

提出的H-Score预测框架包括3个阶段：1）普通核和肿瘤区域分割；2）染色强度描述；3）SINI和SITI的构建，并且通过区域注意力多列卷积神经网络（Region Attention Multi-column Convolutional Neural Network, RAM-CNN）来预测最终的H-Score。框架结构的基本原理是：因为核的数量，肿瘤核的数量和肿瘤核的染色强度个数是预测H-Score的有用信息。因此，作者提出包含这些信息的两个区域掩码。与对染色强度分类人工分界设置不同，作者保持了染色强度的连续描述。仅将有益于预测H-Score的信息提供给深度CNN来预测输入图像的H-Score。这与很多文献中直接将整个图像丢入CNN，而不管区域是否有用的工作不同。

对于正染色像素，为了保留正核的形态学，$I_{la}(m,n)$与原始图像的亮度组件相同；对于负染色像素，在强染色像素（黑蓝颜色）赋予更高的$I_{la}(m,n)$值，赋予更弱染色像素（更亮颜色）更低的值。为了清晰地分离正负像素，往负染色像素中添加了255的偏置，正负像素值将会很清晰地被$I_{la}(m,n)$分离。当$I_{la}(m,n)\leq 255$，它是正染色像素。

使用两个FCN来提取核数量和肿瘤核数量，一个FCN用于分割包括所有核的前景，另一个用于分割仅有肿瘤核的区域。为了分割肿瘤区域，作者对肿瘤TMA图像使用了手工设计的像素层级标签来训练FCN；迁移学习策略被用于普通核检测，训练数据从三个不同的数据集中获取。

##### 词汇

1. histochemical 组织化学
2. microarray 微阵列
3. nuclei activity 核活性
4. semi-quantitative   半定量
5. positively stained nuclei 正染色核
6. on par with  与。。。相当
7. enotype 基因型 
8. phenotype 表型
9. Gene Expression Profiling  （GEP）基因表达谱
10. antigens 抗原
11. Clinical decision making   临床决策
12. available treatment options   可用的治疗方案
13. Diaminobenzidine (DAB)  二氨基联苯胺（DAB）
14. Human Epidermal Growth Factor Receptor  2 (HER2) 人表皮生长因子受体
15. rationale 基本原理

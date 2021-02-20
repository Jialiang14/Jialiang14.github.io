---

layout: post

title: 训练神经网络的技巧

category: 技术

tags: React

keywords:  tips and tricks to train neural networks

---

本篇博客是[“Tip and tricks to train neural networks”][]的中文翻译，仅作为个人的笔记，以及锻炼翻译技巧。

#### 1 通用技巧

首先，如果不确定事情该怎么做，请查阅Pytorch文档(https://pytorch.org/docs/  )。在很多情况下，你都能找到问题答案。

##### 1.1 分析数据

确保了解你要处理的数据集的性质，因为这些性质可以指导你设计你的模型和训练过程。

**数据是否需要预处理？** 当模型的输入和输出值处在相同的数量级时，神经网络可以学得很好。如果你的数据不符合上述条件，你可能需要重新调整或偏移数据中的特征来满足这些特征。

**数据是否对称** 如果数据集是对称的，那么这有助于设计你的模型（不太明白为什么数据的对称性有何作用）。例如，图像通常具有平移对称性，因此利用卷积层的优势通常是一个很好的选择。如果存在这种对抗性，那么可以通过数据增强的方法扩充数据集。

##### 1.2 考虑结构

网络结构（网络层的数量、类型、宽度、激活函数等....）对模型的训练和最终性能有巨大的影响。有时细微的改变会决定模型能否收敛。在实践中研究这些影响，以下是几点建议：

**从小模型开始**：通常从小模型开始，并逐渐增加模型的复杂性。小模型可以快速训练并和迭代。不如大模型复杂。

**网络的宽度和深度都重要**：同时考虑模型的宽度和深度。有时可以相互衡量，但是这样做有一定的局限性。模型太浅会导致无法学习到足够的特征（表示），或网络层不够大（除表达任务外，神经元少的层很难优化）。

**特殊层不是万能的**：卷积层或LSTM的特殊层可以利用数据对称的优势（如空域和时域）。如果你的数据缺少这些对称性，使用这些特殊层可在能会适得其反。

**考虑梯度流**： 网络的所有部分是否至少有一条损失路径（在计算图中），梯度是否可以通过损失路径而不会出现梯度消失？高度饱和的激活函数如sigmoids和tanh不应该堆叠，因为它们会压缩梯度。而在其他极端ResNet中，例如将每个残差块的输出直接连接到损失。

##### 1.3 训练习惯

以下技巧是一些训练神经网络通用的好技巧。

**使用验证集** 为避免过拟合，应将数据集分割成训练集和验证集。仅在训练集中训练模型，并且在验证集中使用验证集来评估需要如何更改。模型总是在训练集数据上有好的性能，但是验证集可以很好地反应模型的泛化性。

**保留测试集** 保留一些数据作为测试集，以便在训练和验证集微调后对模型进行最后的评估。

**在训练时Shuffle数据集** 在每个训练轮次前，在将数据分割成mini-batch前打乱训练数据（Pytorch中在Dataload中指定`shuffle=True`即可）。这样可以确保训练过程不会过度拟合数据集中元素的精确顺序（或防止随机梯度下降收敛而照成损失，因为不平衡的mini-batch会在优化过程中引入噪声）。

**一次只更改一件事，并跟踪改变** 在迭代地设计网络时，最好每次只改动一个部分，并跟踪这个改动。这种方式可以精确地显示出每个改动的影响，也容易丢弃不成功的想法。

**从小数据集开始** 在开始长时间训练前，先在小数据集（数据集的子集）上确保模型可以正确运行。这可以避免因小bug导致快结束训练时出错而浪费时间。

#### 2 分析网络无效的原因

##### 2.1 使用Pytorch解决常见的bug

使用Pytorch时，有些常见的bugs很容易解决，如果不清楚bug的原因，可能会导致神经网络无法正确训练。可以从以下几个方面检查：

**确保优化器的设置** 通过在初始化时将`model.parameters()`作为参数传递来确保优化器已正确地对模型参数进行了初始化。

**不要忘记归零梯度** 在调用损失的`.backward()`前应该调用模型的`.zero_grad()`。否则当前迭代的梯度会与前一次迭代的梯度相加，导致模型执行不适当的训练轨迹训练（梯度下降方向出错）。

**不要使用大的mini-batch** 太大的mini-batch会使计算资源溢出，特别是在训练的模型很大时候。这可能会大大地降低模型地训练速度，甚至完全崩溃。

**不要累积变量** 如果你要存储网络的输出值或损失值，确保调用了`.item()`（对于数值数据）或`.detach()`（对于tensor）并且使用它们的返回值。否则，这将阻止pytorch在每次迭代时从内存中释放计算图，并且将快速占满计算机的RAM，并显著的降低其速度。

##### 2.2 模型似乎没学到任何东西

模型没有学到任何东西的原因

**检查学习率** 使用小学习率的优化器会导致模型学习很慢。在另一方面，太大的学习率会导致模型完全不稳定。通常最佳学习率可以高度依赖于所有因素，包括网络的结构和mini-batch

**检查损失计算** 损失实际上可以计算出预期的结果吗？微小的bug如符号错误将会导致计算的梯度变得毫无意义。

**模型是否正确的初始化** 如果更改了pytorch默认初始化，请确保改变是正确的。不恰当的初始化会导致模型从开始就错了。

**增加网络的能力** 相对于任务，模型不够强大，从而无法学习到好的特征。尝试添加层，或者增加了隐藏层的宽度。

##### 2.3 网络过拟合

网络过拟合通常是指训练性能极大超过验证性能。在这种情况下，网络开始学习数据集的特点，而不是寻找其潜在的模式。

**简化** 减少层的个数直到不再出现过拟合。然后慢慢增加网络的复杂性。

**添加正则化** 正则化方法如对网络权重添加惩罚权重、优化器的权重衰减、dropout和batch norm有助于提高网络的泛化性。它们还会严重损害整体性能，因此能不用尽量不用。

**数据增强** 如果数据是对称的，那么利用数据增强有助于提高网络泛化性能。



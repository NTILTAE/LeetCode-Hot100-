## 用AI学AI

### 沉浸式翻译

doubao 1.5 lite                                      Claude 4 (用Artifact做可视化资料)

DeepSeek(火山)                                    Gemini 2.5 (用好搜索/DeepResearch)

GLN-4-flsah (开箱即用)                       DeepSeek R1+搜索 (问题的详细解释)

## 视频易上手书籍成体系

### 视频教程：

[吴恩达的机器学习/AI课程](https://www.bilibili.com/video/BV164411b7dx/?spm_id_from=333.337.search-card.all.click&vd_source=075169d629dd3ea1a77832039b03930a)

[李宏毅：生成式AI时代下的机器学习（2025）](https://www.bilibili.com/video/BV1SgK7zcE3Y/?spm_id_from=333.337.search-card.all.click&vd_source=075169d629dd3ea1a77832039b03930a)

[B站：李沐论文精读系列](https://space.bilibili.com/1567748478/lists/32744?type=season)

[B站：3Blue1Brown的数学与神经网络介绍部分](https://www.bilibili.com/video/BV1Tq37z3EcU/?spm_id_from=333.337.search-card.all.click&vd_source=075169d629dd3ea1a77832039b03930a)

[B站：王木头学科学](https://space.bilibili.com/504715181?spm_id_from=333.337.0.0)

[B站：Zomi](https://space.bilibili.com/517221395?spm_id_from=333.337.0.0)

### 书籍

《深度学习入门：基于Python的理论与实现》

《the document is all your need》

《动手学深度学习（PyTorch版》

《深度学习的数学》

### 小建议

80%内容在英文内容上

## 基础设施的演进

**Brook-> COTS-> The Better Lession-> Scaling Law->**

### Scaling Law，上帝的指挥棒（2020.01）

[  论文名：Scaling Laws for Neural Language Models]([https://arxiv.org/abs/2001.08361](vscode-file://vscode-app/c:/Program%20Files/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html))

通常指的是在深度学习领域发现的“规模定律”，即随着模型参数数量、数据量和计算量的增加，模型性能会以某种规律性提升。这一规律被称为“上帝的指挥棒”，意味着只要不断扩大模型和数据规模，模型的表现就会持续提升。这一发现最早在 2020 年初被 OpenAI 等团队系统性提出，对 AI 研究和工业界产生了深远影响。

简而言之，Scaling Law 告诉我们：在一定范围内，模型越大、数据越多，AI 的能力就越强。这就像“上帝的指挥棒”一样，为 AI 发展指明了方向。

### The Hardware Lottery 当我们回顾GPU时代（2020.09）

 [ The Hardware Lottery](https://arxiv.org/abs/2009.06489)

“The Hardware Lottery” 是 AI 领域著名的观点，最早由 Sara Hooker 在 2020 年 9 月提出。它指出，AI 研究和深度学习的发展，常常受到硬件条件的极大影响。所谓“硬件彩票”，指的是某些算法或模型之所以流行和成功，并不完全因为它们理论上最优，而是因为它们恰好适配了当时主流的硬件（如 GPU）。

回顾 GPU 时代，深度学习的爆发与 GPU 的并行计算能力密不可分。许多神经网络架构（如卷积神经网络 CNN、Transformer 等）能够高效运行，正是因为 GPU 擅长大规模矩阵运算。如果当时主流硬件不是 GPU，而是其他类型的加速器，AI 领域可能会流行完全不同的算法和模型。

DeepSeek硬件彩票，比Open AI用更少的显卡，更少的数据

因此，“The Hardware Lottery” 提醒我们，AI 研究的方向和成果，往往受到硬件发展的“指挥棒”影响。理解这一点，有助于我们更全面地看待技术选择和创新的偶然性。

### LAION-5B，开源社区的英雄主义（2022.10）

[  LAION-5B: An open large-scale dataset for training next generation image-text models]([https://arxiv.org/abs/2210.08402](vscode-file://vscode-app/c:/Program%20Files/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html))

LAION-5B 是 2022 年开源社区发布的超大规模多模态数据集，包含约 50 亿对图像与文本描述。它的出现极大推动了 AI 领域，尤其是大模型（如 CLIP、Stable Diffusion 等）的训练和创新。

“开源社区的英雄主义”体现在以下几个方面：

1. **资源共享** ：LAION-5B 由全球志愿者和研究者共同构建，免费开放给所有人使用，降低了 AI 研究的门槛。
2. **推动创新** ：有了这样的大规模数据集，更多团队和个人可以训练自己的多模态模型，促进了 AI 技术的多样化和快速发展。
3. **协作精神** ：项目汇聚了全球开源社区的力量，展现了协作、无私和开放的精神。
4. **影响深远** ：LAION-5B 成为许多知名 AI 模型的基础数据集，推动了生成式 AI、图文检索等多个方向的突破。

## 模型结构的演进

**读论文是要对论文有整体印象，是干嘛的，遇到什么问题，找到论文的动机直觉**

AlexNet-> Attention-> distlling-> ResNet-> Transformer-> PPO-> XLNet-> RoFormer-> LoRA-> CoT

### AlexNet，深度学习的开端（2012.10）

  **[ImageNet Classification with Deep Convolutional Neural Networks](https://papers.nips.cc/paper/2012/hash/c399862d3b9d6b76c8436e924a68c45b-Abstract.html)**

  作者：Alex Krizhevsky, Ilya Sutskever, Geoffrey E. Hinton

AlexNet 是 2012 年 10 月由 Alex Krizhevsky 等人提出的深度卷积神经网络模型。它在 ImageNet 图像识别竞赛中以巨大优势夺冠，极大推动了深度学习在计算机视觉领域的发展，被认为是现代深度学习浪潮的开端。

AlexNet 的创新主要体现在以下几个方面：

1. **深层结构** ：采用了 8 层神经网络，包括6250万参数（5 层卷积层 + 3 层全连接层），远超当时主流模型的深度。
2. **ReLU 激活函数** ：首次大规模使用 ReLU替代传统神经元，有效缓解了梯度消失问题，加快了训练速度。
3. **GPU 加速** ：利用 GPU 进行大规模并行计算，使得训练大模型成为可能。
4. **数据增强与 Dropout** ：通过数据增强和 Dropout 技术，有效提升了模型的泛化能力，减少了过拟合。

AlexNet 的成功标志着深度学习时代的到来，开启了神经网络在图像、语音、自然语言处理等领域的广泛应用。

### Attention的开端（2014.09）

 [  Neural Machine Translation by Jointly Learning to Align and Translate](https://arxiv.org/abs/1409.0473)

   **作者** ：Dzmitry Bahdanau, Kyunghyun Cho, Yoshua Bengio

1. 背景

在 2014 年之前，神经机器翻译（NMT）主要采用编码器-解码器（Encoder-Decoder）结构。编码器将整个输入句子压缩成一个固定长度的向量，解码器再根据这个向量生成目标句子。这种方法在处理长句子时效果不佳，因为固定向量难以完整表达所有信息。

2. 主要创新

Bahdanau 等人提出了 **注意力机制（Attention Mechanism）** ，其核心思想是：
在生成目标句子每个词时，模型可以“动态地”关注输入句子的不同部分，而不是只依赖一个固定向量。

3. 机制原理

* **对齐（Alignment）** ：模型在生成目标词时，会计算该词与输入句子每个词的相关性（即“注意力权重”）。
* **加权求和** ：用这些权重对输入句子的隐藏状态做加权求和，得到一个“上下文向量”。
* **动态上下文** ：每生成一个目标词，都会重新计算一次注意力分布，实现动态关注。

4. 结构示意
5. **编码器** ：对输入句子每个词编码，得到一系列隐藏状态。
6. **解码器** ：每步生成目标词时，结合前一步状态和当前上下文向量。
7. **注意力层** ：根据当前解码器状态，计算与所有编码器隐藏状态的相关性，得到注意力分布。
8. 优势与影响

* **提升长句翻译效果** ：模型不再受限于固定向量，能更好处理长句和复杂句。
* **可解释性强** ：注意力权重可视化后，可以看到模型在翻译时“关注”了输入句子的哪些部分。
* **广泛应用** ：Attention 机制成为后续 Seq2Seq、Transformer、BERT 等模型的基础模块

### 蒸馏，祖师爷Hinton再度出手（2015.03）

“蒸馏”（Distillation）是 Geoffrey Hinton 等人在 2015 年提出的一种深度学习模型压缩与知识迁移方法。其核心论文是[《Distilling the Knowledge in a Neural Network》（2015.03）](https://arxiv.org/abs/1503.02531)，作者包括 Geoffrey Hinton、Oriol Vinyals 和 Jeff Dean。

1. 背景

深度神经网络（DNN）通常参数量大、计算资源消耗高，不适合部署在资源受限的设备（如手机、嵌入式系统）上。如何在保证模型性能的同时，减小模型体积，是实际应用中的重要问题。

2. 蒸馏的核心思想

蒸馏（Knowledge Distillation）是一种**模型压缩**技术。它的基本思路是：

* 先训练一个大型、性能强的“教师模型”（Teacher）。
* 再用教师模型的输出（不仅仅是最终标签，还包括“软标签”——即各类别的概率分布）来训练一个较小的“学生模型”（Student）。
* 学生模型通过模仿教师模型的输出，能够学到更丰富的知识，从而在体积更小的情况下，获得接近甚至超过教师模型的性能。

3. 技术细节

* **软标签（Soft Targets）** ：传统训练只用真实标签（如 one-hot），而蒸馏用教师模型输出的概率分布作为训练目标，这些概率包含了类别之间的相似性信息。
* **温度参数（Temperature）** ：通过调整 softmax 的温度参数，可以让输出概率分布更平滑，便于学生模型学习。
* **损失函数** ：学生模型的损失函数通常包括对真实标签的交叉熵损失和对教师输出的蒸馏损失。

4. 优势与应用

* **模型压缩** ：大幅减小模型体积，便于部署。
* **知识迁移** ：学生模型能继承教师模型的“暗知识”（如类别间的微妙关系）。
* **灵活性强** ：可以用于不同结构的模型之间的知识迁移。

5. 影响

蒸馏技术自提出后，广泛应用于模型压缩、迁移学习、模型集成等领域，成为深度学习模型落地的重要工具。它也启发了后续如多教师蒸馏、对抗蒸馏等一系列研究。

### ResNet，比深更深（2015.12）

ResNet（Residual Neural Network，残差网络）是由何恺明等人在 2015 年 12 月提出的深度神经网络架构，论文名为[《Deep Residual Learning for Image Recognition》](https://arxiv.org/abs/1512.03385)。ResNet 的出现极大推动了深度学习模型的“加深”，解决了深层网络训练中的退化（degradation）和梯度消失问题，被认为是现代计算机视觉领域的里程碑。

1. 背景

在 AlexNet、VGG 等模型之后，研究者发现：

* 网络越深，理论上表达能力越强，但实际训练时，深层网络反而容易出现准确率下降（退化问题）。
* 主要原因是梯度消失/爆炸，导致深层网络难以优化。

2. 核心思想

ResNet 的核心创新是 **残差连接（Residual Connection）** ，即引入“捷径”（shortcut）或“跳跃连接”（skip connection）：

* 传统网络：输出 = F(x)
* ResNet：输出 = F(x) + x

其中 F(x) 是一系列卷积、激活等操作，x 是输入。这样，网络只需学习“残差”部分 F(x)，而不是完整的映射。

3. 结构与实现

* **残差块（Residual Block）** ：每两层或三层卷积后，将输入直接加到输出上。
* **极深网络** ：ResNet 可以轻松堆叠 50 层、101 层、152 层甚至更深，性能持续提升。
* **Bottleneck 结构** ：在更深的网络中，采用 1x1 卷积降维和升维，减少计算量。

4. 优势与影响

* **极大缓解梯度消失/爆炸** ，使超深网络可训练。
* **大幅提升图像识别准确率** ，ResNet 在 2015 年 ImageNet 竞赛中夺冠。
* **通用性强** ，被广泛应用于目标检测、分割、NLP 等领域。
* **启发后续架构** ，如 DenseNet、Transformer 等也借鉴了残差思想。

### Transformer来了！拉开一个时代的序幕（2017.06）

解决翻译的问题

Transformer 是由 Vaswani 等人在 2017 年 6 月提出的深度学习模型，论文名为[《Attention Is All You Need》](https://arxiv.org/abs/1706.03762)。Transformer 的出现，彻底改变了自然语言处理（NLP）和人工智能领域，被认为是“拉开一个时代序幕”的划时代工作。

一、提出背景

在 Transformer 出现之前，主流的序列建模方法是循环神经网络（RNN）、长短时记忆网络（LSTM）和卷积神经网络（CNN）。这些方法存在以下问题：

* **难以并行计算** ：RNN 结构决定了序列只能逐步处理，训练和推理速度慢。
* **长距离依赖难捕捉** ：RNN 在处理长序列时，信息传递容易衰减，难以建模远距离依赖关系。

二、核心创新

Transformer 完全基于 **自注意力机制（Self-Attention）** ，摒弃了 RNN 和 CNN 结构，实现了高效的并行计算和强大的序列建模能力。

1. 自注意力机制（Self-Attention）

* 每个输入位置都能“关注”序列中所有其他位置，动态分配权重，捕捉全局依赖关系。
* 通过 Query、Key、Value 三组向量计算注意力分数，得到加权和。

2. 多头注意力（Multi-Head Attention）

* 将自注意力机制并行分成多个“头”，每个头学习不同的子空间特征，增强模型表达能力。

3. 编码器-解码器结构

* **编码器（Encoder）** ：将输入序列编码为一组高维表示。
* **解码器（Decoder）** ：根据编码器输出和已生成的目标序列，逐步生成目标输出。

4. 位置编码（Positional Encoding）

* 由于 Transformer 不含序列结构，使用位置编码为每个输入添加位置信息，使模型感知顺序。

三、优势与影响

* **高效并行** ：所有位置可同时计算，极大提升训练速度。
* **强大建模能力** ：能捕捉长距离依赖，适合处理长文本。
* **通用性强** ：不仅适用于 NLP，还广泛应用于图像、语音、蛋白质结构等领域。
* **引领大模型时代** ：BERT、GPT、T5、ViT 等众多知名模型均基于 Transformer 架构。

cccc

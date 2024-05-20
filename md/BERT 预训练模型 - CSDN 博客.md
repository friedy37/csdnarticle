> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/weixin_63595187/article/details/131388243?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7ERate-1-131388243-blog-131343535.235%5Ev43%5Epc_blog_bottom_relevance_base9&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7ERate-1-131388243-blog-131343535.235%5Ev43%5Epc_blog_bottom_relevance_base9&utm_relevant_index=1)

参考资料  
[BERT 模型解读（附 pytorch 代码） - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/404628038)  
[Bert 和 GPT - 魔法学院小学弟](http://124.220.164.99:8090/archives/bert%E5%92%8Cgpt)  
[BERT 模型的详细介绍_IT 之一小佬的博客 - CSDN 博客](https://blog.csdn.net/weixin_44799217/article/details/115374101?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522168760614716782425175458%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=168760614716782425175458&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-2-115374101-null-null.142%5Ev88%5Econtrol_2,239%5Ev2%5Einsert_chatgpt&utm_term=bert%E6%A8%A1%E5%9E%8B&spm=1018.2226.3001.4187)

一、简述
----

[BERT](https://so.csdn.net/so/search?q=BERT&spm=1001.2101.3001.7020) (Bidirectional Encoder Representations from Transformers) 是一种预训练语言模型，由 Google 在 2018 年提出以无监督的方式利用大量无标注文本「炼成」的语言模型，它是一种基于 Transformer 网络结构的模型，其架构采用的是 Transformer 中的 Encoder 结构。[BERT 模型](https://so.csdn.net/so/search?q=BERT%E6%A8%A1%E5%9E%8B&spm=1001.2101.3001.7020)的提出可以说是自然语言处理领域的一次重大突破，它在许多自然语言处理任务上取得了最先进的效果，包括问答、文本分类、命名实体识别、语义相似度等。

BERT 模型采用**预训练和微调**两个阶段。

在预训练阶段，BERT 模型会利用大量的无标签语料来学习语言表示，其中包括两个**并行**的任务：Masked Language Modeling 任务（MLM）和 Next Sentence Prediction 任务（NSP）。 MLM 是指在输入语句中随机选择一些单词并将它们替换成掩码（例如 [Mask]），让模型来预测这些掩码的正确词语，以此来训练模型对上下文的理解能力。 NSP 是在双向语言模型的基础上额外增加了一个句子级别的连续性预测任务，即判断两个语句之间的逻辑关系，比如是否是连续的，即判断第二个语句是否是第一个语句的下一句。这个任务可以帮助模型学习语句之间的关系，进而提高模型的推理能力。

BERT 模型通过对 Masked LM 任务和 Next Sentence Prediction 任务进行联合训练，使模型输出的每个字 / 词的向量表示都能尽可能全面、准确地刻画输入文本（单句或语句对）的整体信息，为后续的微调任务提供更好的模型参数初始值。

在微调阶段，BERT 模型会使用标注数据进行微调，**以适应不同的自然语言处理任务**。例如，在问答任务中，BERT 模型会将问题和一篇文章作为输入，并输出答案的位置和内容。

BERT 模型的主要优势在于它的预训练阶段可以使用大量的**无标签语料**进行训练，从而提高了模型的泛化能力。此外，BERT 模型还采用了双向编码器的结构，允许模型同时考虑左右两侧的上下文信息，进一步提高了模型的效果。  
总的来说，BERT 模型的提出是自然语言处理领域的一次重大进展，它不仅在学术界受到广泛关注，也在工业界得到了广泛应用。它的本质是**通过预训练学习文本更好的向量表示，通过微调来适用 NLP 领域不同的任务**。

二、BERT 研究的动机
------------

BERT 的出现时 NLP 领域的转折点，从此进入了 fine-tuning 的新时代。在 BERT 之前，许多 NLP 任务都是采用单独的模型或特征提取方法来完成的。而 BERT 的出现为 NLP 领域带来了巨大的变革，因为它具有更好的通用性和性能。接下来详细解释一下 BERT 模型研究的动机：

**上下文敏感性**：在自然语言处理中，理解上下文对于模型准确解读语义至关重要。以往的模型如 word2vec 和 GloVe 等，只能够生成静态的词向量，即一个词在不同的上下文中具有相同的向量表示。BERT 的研究动机之一便是提高模型对上下文的敏感性，实现动态词向量表示。

**预训练和微调**：过去的 NLP 任务通常采用特定任务的模型，这意味着每个任务都需要从头开始训练模型。BERT 模型提出了预训练和微调的思想。首先在大规模语料库上进行预训练，学习通用的语言知识。然后将预训练好的模型进行微调，适应特定的 NLP 任务。这种方法大大提高了模型的训练效率和性能。

**双向编码**：传统的自然语言处理模型通常采用单向或双向的顺序模型，例如 RNN、LSTM 和 GRU。然而，这些模型无法完全捕捉到上下文信息。BERT 引入了双向 Transformer 编码器，可以同时考虑到词汇在上下文中的前后关系，从而更好地捕捉句子中的语义信息。

**通用性**：BERT 模型的设计初衷是为了提供一个通用的预训练模型，以适应各种 NLP 任务。因此，BERT 模型在研究动机上非常关注通用性。事实证明，BERT 在很多 NLP 任务上都取得了显著的性能提升，如情感分析、命名实体识别、问答系统等。

**提高性能**：BERT 的研究动机还包括在各种 NLP 任务上取得更高的性能。在 BERT 发布之后，它在多个任务上刷新了记录，如 GLUE、SQuAD 和 SWAG 等基准测试。

总之，BERT 模型研究的动机在于提高上下文敏感性、利用预训练和微调的方法提高训练效率、利用双向 Transformer 编码器捕捉更丰富的上下文信息、实现通用性以适应各种 NLP 任务，以及在各种 NLP 任务上提高性能。这些动机共同推动了 BERT 模型的发展，使其成为了当今自然语言处理领域的重要基石。

三、预训练和微调
--------

BERT 模型的组成部分，包括输入、中间组件和输出结果，如下图所示：  
![](https://img-blog.csdnimg.cn/3e159aff730e48938c19846535ce4b36.png)

BERT 模型的输入由三个部分组成：Token Embeddings、Segment Embeddings 和 Position Embeddings。

*   Token Embeddings：将输入文本中的每个单词或子词转换为固定大小的向量表示。BERT 使用 WordPiece Tokenizer 将输入文本分割成子词。
    
*   Segment Embeddings：用于区分两个句子，主要用于句子对任务，例如问答或自然语言推理。在句子对任务中，两个句子被拼接在一起，然后用特殊标记（如 [SEP]）分隔。
    
*   Position Embeddings：由于 BERT 模型中的 Transformer 编码器缺乏位置感知能力，因此需要加入位置信息。位置嵌入通过为输入序列中的每个位置分配一个向量来实现。
    

这三个嵌入向量会逐元素相加，得到一个综合的嵌入向量表示，用于输入 BERT 的 Transformer 编码器。Bert 的输入是两个句子拼接在一起的，这是因为 BERT 的设计初衷是为了处理各种自然语言处理任务，其中许多任务涉及到句子对，例如问答、自然语言推理（NLI）和语义文本相似度（STS）等。为了使模型能够处理这些任务，BERT 采用了两个句子拼接在一起的输入方式。 在这种输入表示中，两个句子（句子 A 和句子 B）使用特殊分隔符 [SEP] 进行分隔，并在句子对的开头添加特殊标记 [CLS]。同时，通过引入 Segment Embeddings，BERT 能够区分句子 A 和句子 B。这种输入表示方式使得 BERT 在预训练阶段就能同时学习单句子和双句子任务的语义表示。 值得注意的是，尽管 BERT 的输入设计可以处理两个句子，但它也可以灵活地处理单句子任务。对于单句子任务，可以只输入一个句子，并在句子开头添加[CLS] 标记，同时仍然使用 Segment Embeddings。 这种输入表示方法使得 BERT 可以在预训练和微调阶段处理各种单句子和双句子任务，提高了模型的通用性和适用范围。

BERT 框架的核心其实就是 Transformer 的 Encoder 架构。Transformer 的 Encoder 由多层自注意力机制（Self-Attention）和前馈神经网络（Feed-Forward Neural Network）组成的堆叠层。在自注意力机制中，每个词的表示都会根据整个输入序列中的其他词的上下文进行调整。这使得 BERT 能够充分捕捉句子中的**双向**上下文信息。BERT 模型中的 Transformer Encoder 的数量取决于具体的模型变体，不同的变体有不同数量的 Encoder。 B E R T B A S E : L = 12 , H = 768 , A = 12 , T o t a l P a r a m e t e r s = 110 M B E R T L A R G E : L = 24 , H = 1024 , A = 16 , T o t a l P a r a m e t e r s = 340 M

$$\begin{aligned} BERT_{BASE}&:L=12,H=768,A=12,TotalParameters=110M\\ BERT_{LARGE}&:L=24,H=1024,A=16,TotalParameters=340M \end{aligned}$$

BERTBASE​BERTLARGE​​:L=12,H=768,A=12,TotalParameters=110M:L=24,H=1024,A=16,TotalParameters=340M​

论文原文中，作者使用了 12 层和 24 层的 Transformer Encoder，组装了两套模型。其中层的数量（也就是 Transformer Encoder 的数量）为 L，隐藏层的维度为 H，自注意头数为 A，论文中字典大小 30k。

**与 Transformer 的 Encoder 相比，BERT 的 Transformer Encoder 端输入的向量表示多了 Segment Embedding**

经过若干层 Transformer 编码器处理后，BERT 会输出一个向量序列，与输入序列等长。这个向量序列可以用于各种下游任务。 例如分类层、序列标注层或者生成层等。这个附加层的输出将作为任务的最终结果。 例如，对于文本分类任务，BERT 输出的第一个位置（对应特殊标记 [CLS]）的向量会被送入一个全连接层，然后进行分类。对于序列标注任务，每个输出位置的向量都会进入一个全连接层，进行逐个位置的标注。

BERT 模型采用了两阶段的训练过程：预训练（Pre-training）和微调（Fine-tuning）。这种训练策略的目的是将通用的语言知识和特定任务的知识结合起来，以提高模型的性能和泛化能力。下面详细解释这两个阶段

### 3.1 预训练阶段

预训练（Pre-training）阶段的目标是让 BERT 模型学习通用的语言知识。在这个阶段，模型使用无监督学习的方法，在大规模的未标注文本数据（例如，维基百科等）上进行训练。预训练阶段采用了两个**并行**的任务 Masked LM 任务和 NSP 任务，为多任务学习。  
![](https://img-blog.csdnimg.cn/90600a8cdb85451c9e0e251a0b0cf84f.png)

#### 3.1.1 MLM 任务

在这个任务中，模型需要预测句子中被随机遮挡的词汇，其实就是 “**完形填空**” 任务。这迫使模型学习如何根据上下文生成词汇的表示。在这个任务中，被随机遮挡的词汇作为模型训练的真值（Label），这个真值与有监督训练中的真值不同，它不是人工标注的，所以被成为**无监督学习**。这是个典型的 Denosing Autodecoder 的思路，那些被 mask 掉的单词就是在**输入侧加入噪音**。类似 BERT 这种预训练模式，称为 DAE LM。因此总结来说，BERT 模型的 [MASK] 标记就是引入噪音的手段。

[DAE LM]：关于这种预训练模式，优点是它能比较自然地融入双向语言模型，同时看到被预测单词的上下文，然而缺点也很明显，主要在输入侧引入 [MASK] 标记，导致预训练阶段和 fine-tuning 阶段不一致的问题。

Maked LM 构建了语言模型，简单来说就是**随机遮盖或替换**一句话里面任意的字或词，然后让模型通过上下文预测被遮盖或者替换了的部分，之后**做 Loss 的时候也只计算被遮盖部分的 Loss**。具体操作如下：

1.  随机把一句话中 15% 的 token 换成以下内容：
    1.  这些 token 中有 80% 的几率替换成`[mask]`。如`my dog is hairy->my dog is [mask]`
    2.  有 10% 的几率被替换成一个其他的 token，如`my dog is hairy->my dog is apple`
    3.  有 10% 的几率保持原样，如`my dog is hairy->my dog is hairy`
2.  让模型**预测和还原**被遮盖掉或替换掉的部分，当计算 Loss 时，只计算在第一步里被**随机遮盖或替换**的部分，其余部分不做损失，其余部分无论输出什么都不重要。

这样的好处是 BERT 并不知道 `[MASK]` 替换的是哪一个词，而且任何一个词都有可能是被替换掉的，比如它看到的 apple 可能是被替换的词。这样强迫模型在编码当前时刻词的时候不能太依赖当前的词，而要考虑它的上下文，甚至根据上下文进行 “纠错”。比如上面的例子中，模型在编码 apple 时，根据上下文 my dog is，应该把 apple 编码成 hairy 的语义而不是 apple 的语义。  
![](https://img-blog.csdnimg.cn/671a5258cde146e4838c64384e88bd71.png)

显然，这样 BERT 中的 mask 的思想来源于 CBOW。接下来辨析一下两者之间的区别。  
**相同点**：  
- CBOW 的核心思想是给定上下文，根据上文 context-before 和下文 context-after 去预测 input word。而 BERT 实际上也是这么去做的，但 BERT 的做法是给定一个句子，会随机 mask15% 的词，然后让 BERT 来预测这些 mask 的词。  
**不同点**：  
- 首先在 CBOW 中，每个单词都会成为 input word，而 BERT 不是这么做的，如果这么做的话那么训练数据就太大了，而且训练时间会非常长。  
- 其次对于输入数据部分，CBOW 中的输入数据只有待预测单词的上下文，而 BERT 的输入是带有 [MASK] token 的“完整” 句子，也就是说 BERT 在输入端将待预测的 input word 用[MASK] token 代替了。  
- 另外，通过 CBOW 模型训练后，每个单词的 word embedding 是唯一的，因此并不能很好的处理一词多义的问题，而 BERT 模型得到的 word embedding(token embedding) 融合了上下文的信息，就算是同一个单词，在不同的上下文环境下，得到的 word embedding 是不一样的。

*   **词袋模型到 word2vec 的改进**
    
    *   词袋模型 (Bag-of-words model) 是将一段文本（比如一个句子或是一个文档）用一个 “装着这些词的袋子” 来表示，这种表示方式不考虑文法以及词的顺序。「而在用词袋模型时，文档的向量表示直接将各词的词频向量表示加和」。通过上述描述，可以得出词袋模型的两个缺点：
        
        *   词向量化后，词与词之间是有权重大小关系的，不一定词出现的越多，权重越大。
        *   词与词之间是没有顺序关系的。
    *   而 word2vec 是考虑词语位置关系的一种模型。通过大量语料的训练，将每一个词语映射成一个低维稠密向量，通过求余弦的方式，可以判断两个词语之间的关系，word2vec 其底层主要采用基于 CBOW 和 Skip-Gram 算法的神经网络模型。
        
    
    因此，综上所述，词袋模型到 word2vec 的改进主要集中于以下两点：
    
    *   考虑了词与词之间的顺序，**引入了上下文的信息**
    *   得到了词更加准确的表示，其**表达的信息更为丰富**
*   **word2vec 到 BERT 的改进**  
    word2vec 到 BERT 的改进之处其实没有很明确的答案，BERT 的思想其实很大程度上来源于 CBOW 模型，如果从准确率上说改进的话，BERT 利用**更深的模型，以及海量的语料**，得到的 embedding 表示，来做下游任务时的准确率是要比 word2vec 高不少的。实际上，这也离不开模型的 “加码” 以及数据的“巨大加码”。再从方法的意义角度来说，BERT 的重要意义在于给大量的 NLP 任务提供了一个**泛化能力很强的预训练模型**，而仅仅使用 word2vec 产生的词向量表示，不仅能够完成的任务比 BERT 少了很多，而且很多时候直接利用 word2vec 产生的词向量表示给下游任务提供信息，下游任务的表现不一定会很好，甚至会比较差。
    

#### 3.1.2 NSP 任务

我们首先拿到上下文的一个句子对，也就是两个句子。我们要在两个句子之中加入一些特殊的 token：`[CLS]第一句话[SEP]第二句话[SEP]`。也就是在句子开头加一个 [CLS]，在两句话之间和句末加入 [SEP]。  
![](https://img-blog.csdnimg.cn/854d91db45084c24802a8b70bb39da01.png)

**Input**=[CLS] the man went to [MASK] store [SEP]  
he brought a gallon [MASK] milk [SEP]  
**Label**=IsNext

**Input**=[CLS] the man [MASK] to the store [SEP]  
penguin [MASK] are flight ##less birds [SEP]  
**Label**=NoNext

> 上面的 flight ##less 见 [[Transformer 模型]] 中 3.2.3 word Piece Tokenizer

在预训练阶段结束时，BERT 模型将学会理解语法、句法、词汇知识等**通用的语言特征**。

### 3.2 微调阶段

微调（Fine-tuning）阶段的目标是将预训练好的 BERT 模型调整为适应**特定的 NLP 任务**，例如文本分类、命名实体识别、问答系统等。在这个阶段，模型使用**有监督学习**的方法，在特定任务的标注数据上进行训练。

为了适应特定任务，BERT 模型的结构会进行一定的调整。通常情况下，这涉及到**在模型顶部添加一个任务相关的输出层**。例如，在文本分类任务中，可以添加一个全连接层作为输出层，用于预测类别标签。在微调过程中，所有 BERT 模型的参数都会进行更新，以适应特定任务。通过微调，BERT 模型将学会在特定任务上的知识和技能。

这种预训练和微调的训练策略使得 BERT 模型能够在各种 NLP 任务上取得显著的性能提升。预训练阶段学到的通用语言知识可以帮助模型**更好地理解特定任务的语义**，而微调阶段则使模型能够**针对特定任务进行优化**。这两个阶段的结合，使得 BERT 模型具有很好的泛化能力和性能。

四、解决上下文敏感问题
-----------

上下文敏感性（context sensitivity）是指在 NLP 模型在理解和分析文本时，能够捕捉到词汇在不同上下文中的语义变化。在自然语言中，许多词汇具有多种含义，这些含义取决于它们所处的上下文。因此，上下文敏感性对于准确理解和处理自然语言至关重要。

BERT 模型通过以下三个方式解决了上下文敏感性问题：

1.  **双向 Transformer 编码器**：BERT 采用了双向 Transformer 编码器来捕捉上下文信息。Transformer 编码器使用自注意力（self-attention）机制，在处理一个词汇时能够将整个句子的信息都考虑进去。这使得 BERT 能够同时捕捉到一个词汇在上下文中的前后信息，从而实现上下文敏感性。
    
2.  **Masked Language Model (MLM)**：在 BERT 的预训练阶段，使用了被称为 Masked Language Model 的任务。在这个任务中，模型需要预测句子中被随机遮挡的词汇。这要求 BERT 学习如何根据上下文生成被遮挡词汇的正确表示。因此，MLM 任务迫使模型学习上下文敏感性。
    
3.  **动态词向量表示**：动态词向量表示是指在不同上下文中，为同一个词汇生成不同的词向量。这与静态词向量表示相对应，后者指的是在任何上下文中为一个词汇生成相同的词向量。动态词向量表示可以帮助模型更好地理解词汇在不同语境下的多种含义。
    

在 BERT 模型中，由于采用了双向 Transformer 编码器，每个词汇的表示都是基于其在特定上下文中的位置计算得到的。因此，在**不同上下文中，同一个词汇将具有不同的表示**。 举个例子，假设我们有一个单词 “bank”，在英语中它可以表示“银行” 和“河岸”两个不同的概念。在静态词向量表示中，无论 “bank” 出现在哪种上下文中，它都将具有相同的词向量表示。这可能导致模型难以区分它在不同上下文中的不同含义。然而，在 BERT 模型中，由于采用了动态词向量表示，同一个词汇 “bank” 在表示 “银行” 的上下文中和表示 “河岸” 的上下文中将具有不同的词向量表示。这有助于模型更好地理解和区分这个词汇在不同上下文中的含义。

简而言之，**动态词向量表示是一种使模型能够根据上下文为词汇生成不同表示的方法**，这有助于模型在处理具有多种含义的词汇时，根据其所处的上下文生成合适的表示。这种表示方法使得 BERT 模型具有很好的上下文敏感性，从而在各种 NLP 任务中实现了显著的性能提升。

五、针对不同 NLP 特定任务的 fine-tuning
----------------------------

这里有待实验完善

论文原文中给出以下四个例子：语义相似度、多标签分类、机器翻译、文本生成，针对这些特定任务的 BERT 结构微调。  
![](https://img-blog.csdnimg.cn/a8a23fb506ba4a8792b485e5222a6b0b.png)

### 5.1 句子语义相似度

![](https://img-blog.csdnimg.cn/7889b4ee71a64fad980eae6ac329db81.png)

实际操作时，上述最后一句话之后还会加一个 [SEP] token，语义相似度任务将两个句子按照上述方式输入即可，之后与论文中的分类任务一样，将 [CLS] token 位置对应的输出，接上 softmax 做分类即可 (实际上 GLUE 任务中就有很多语义相似度的数据集)。

### 5.2 多标签分类任务

多标签分类任务，即 MultiLabel，指的是一个样本可能同时属于多个类，即有多个标签。以商品为例，一件 L 尺寸的棉服，则该样本就有至少两个标签——型号：L，类型：冬装。

对于多标签分类任务，显而易见的朴素做法就是不管样本属于几个类，就给它训练几个分类模型即可，然后再一一判断在该类别中，其属于那个子类别，但是这样做未免太暴力了，而多标签分类任务，其实是可以**只用一个模型**来解决的。

利用 BERT 模型解决多标签分类问题时，其输入与普通单标签分类问题一致，得到其 embedding 表示之后 (也就是 BERT 输出层的 embedding)，有几个 label 就连接到几个全连接层 (也可以称为 projection layer)，然后再分别接上 softmax 分类层，这样的话会得到 ，最后再将所有的 loss 相加起来即可。这种做法就相当于将 n 个分类模型的特征提取层参数共享，得到一个共享的表示 (其维度可以视任务而定，由于是多标签分类任务，因此其维度可以适当增大一些)，最后再做多标签分类任务。

### 5.3 其他任务

单句分类任务  
![](https://img-blog.csdnimg.cn/2f678ecaa1324d6ab3705ed7f31773e6.png)

QA 问答任务  
![](https://img-blog.csdnimg.cn/cfa296ed23374c01a490ca786255d759.png)

NER 文本标签任务  
![](https://img-blog.csdnimg.cn/578cab257297498886a24b823a0e555e.png)

六、代码实现
------

### 6.1 输入模式

以连续问答为例，相邻句子之间为连续，否则为不连续。初始语料如下所示。

```
text = (
    'Hello, how are you? I am Romeo.\n' # R
    'Hello, Romeo My name is Juliet. Nice to meet you.\n' # J
    'Nice meet you too. How are you today?\n' # R
    'Great. My baseball team won the competition.\n' # J
    'Oh Congratulations, Juliet\n' # R
    'Thank you Romeo\n' # J
    'Where are you going today?\n' # R
    'I am going shopping. What about you?\n' # J
    'I am going to visit my grandmother. she is not very well' # R
)
```

MLM 和 Next Sentence Prediction 两个任务同时进行，为多任务学习，因此在格式处理阶段，需要把两个任务所需要的内容拼成一个 sample。

处理步骤：

1.  需要拼接任意两句话 其中保证连续 / 非连续的比例为 1:1 ； 一个 batch 中，batch/2 个连续，batch/2 个不连续。
2.  根据概率随机替换（以下统称 mask）拼接后句子中 15% 的 token。
3.  padding。
4.  最终为： **[CLS] sentence_a [SEP] sentence_b [SEP] ** 格式，其中 sentence_a 和 sentence_b 部分 15% 的 token 被 mask。

```
def make_data():
    '''
    MLM 和 Next Sentence Prediction 两个任务同时进行，为多任务学习
    1 需要拼接任意两句话 其中保证连续/非连续的比例为 1:1  ； 一个 batch 中，batch/2 个连续，batch/2 个不连续
    2 根据概率随机替换（以下统称 mask）拼接后句子中 15% 的 token，
    -> [cls] sentence_a [sep] sentence_b [sep] [pad] 格式，其中 sentence_a 和 sentence_b 部分 15% 的 token 被 mask
    '''
    continues, not_continues = 0, 0 #记录两句子连续/不连续数量
    batch = []
    
    while((continues < batch_size/2) or (not_continues < batch_size/2)):
        
        sentence_index_1, sentence_index_2 = randrange(len(token_list)), randrange(len(token_list)) #随机抽取句子索引 由于为一问一答，前后连贯。索引连续为连续，否则为不连续
        
        input_ids =  [word2idx['[CLS]']] + token_list[sentence_index_1] + [word2idx['[SEP]']] + token_list[sentence_index_2] + [word2idx['[SEP]']] #索引构成
        segment_ids = [0] * (1 + len(token_list[sentence_index_1]) + 1) + [1] * (len(token_list[sentence_index_2]) + 1) #segment embeddings
        
        #MLM
        num_mask = min(max_num_mask, int(0.15*(len(input_ids)))) #mask数量
        
        candidate_pos = [pos for pos in range(len(input_ids))
                                    if (input_ids[pos] != 1) and (input_ids[pos] != 2)] #候选mask位置。可能的position index中 去除[cls] [sep]
        shuffle(candidate_pos) #shuffle
        
        masked_tokens = [] #被mask的token
        masked_pos = candidate_pos[:num_mask] #被mask的token位置
        for pos in masked_pos:
            masked_tokens.append(input_ids[pos])
            '''
            0.8 mask
            0.1 随机替换任意词
            0.1 不替换
            '''
            if random() < 0.8:    
                input_ids[pos] = 3 #[mask]填充
            elif random() > 0.9:
                while(True):
                    token = randrange(4, vocab_size) #用词表中除了填充词外的词填充
                    if token == input_ids[pos]:
                        continue
                    else:
                        input_ids[pos] = token
                        break
        
        #padding
        '''
        input_ids 填充 max_len - len(input_ids)个
        segment_ids 填充 max_len - len(input_ids)个
        masked_tokens 填充 max_num_mask - num_mask个
        masked_pos 填充 max_num_mask - num_mask个
        '''
        num_pad = max_sequence_length - len(input_ids)
        input_ids.extend([word2idx['[PAD]']]*num_pad)
        segment_ids.extend([word2idx['[PAD]']]*num_pad)
        
        num_pad = max_num_mask - num_mask
        masked_tokens.extend([word2idx['[PAD]']]*num_pad)
        masked_pos.extend([word2idx['[PAD]']]*num_pad)
        
        #continues judge
        '''
        not_continues / continues < batch_size/2 时，添加到batch中，否则不添加
        '''
        if (np.abs(sentence_index_1-sentence_index_2) == 1) and (continues<batch_size/2):
            continues += 1
            batch.append([input_ids, segment_ids, masked_tokens, masked_pos, 1]) #1表示连续
            
        if (np.abs(sentence_index_1-sentence_index_2) != 1) and (not_continues<batch_size/2):
            not_continues += 1
            batch.append([input_ids, segment_ids, masked_tokens, masked_pos, 0]) #0表示不连续
            
    return batch
```

### 6.2 结构

#### 6.2.1 Embedding

word_embedding，segment_embedding，positional_embedding 三重 embedding，结果直接 add。

positional_embedding 不同 Transformer 中固定死，在 BERT 中为可训练参数。

```
class Embedding(nn.Module):
    def __init__(self):
        super(Embedding, self).__init__()
        self.word_embedding = nn.Embedding(vocab_size, embedding_dimension)
        self.segment_embedding = nn.Embedding(n_segments, embedding_dimension)
        self.positional_embedding = nn.Embedding(max_sequence_length, embedding_dimension)
    
    def forward(self, input_ids, segment_ids):
        '''
        input_ids: shape(batch_size, max_sequence_length)
        segment_ids: shape(batch_size, max_sequence_length)
        构造 pos_ids: shape(batch_size, max_sequence_length)
        embedding 过后：shape(batch_size, max_sequence_length, embedding_dimension)
        输出 三者直接add
        '''
        input_ids = torch.LongTensor(input_ids.numpy())
        segment_ids = torch.LongTensor(segment_ids.numpy())
        pos_ids = torch.arange(max_sequence_length)
        pos_ids = pos_ids.expand_as(input_ids)
        return self.word_embedding(input_ids) + self.segment_embedding(segment_ids) + self.positional_embedding(pos_ids)
```

#### 6.2.2 Gelu 激活函数

用在 MLM 任务最后的 Linear 层之前

```
x * 0.5 * (1.0 + torch.erf(x / math.sqrt(2.0)))
```

#### 6.2.3 其他结构和 Transformer 一样

其他就是 Transformer 中的 Encoder

```
class Attention(nn.Module):
    '''
    self-attention
    '''
    def __init__(self):
        super(Attention, self).__init__()
    
    def forward(self, q, k, v, attr_mask):
        '''
        q, k, v: shape(batch_size, n_heads, sequence_length, embedding_dimension)
        attr_mask: shape(batch_size, n_heads, sequence_length, sequence_length)
        '''
        score = torch.matmul(q, k.transpose(-1, -2)) / math.sqrt(q.size(1)) #k为四维张量，不能用转置 k.transpose(-1, -2)
        score.masked_fill(attr_mask, 1e-9)
        score = torch.softmax(score, dim=-1)
        return torch.matmul(score, v)

class Multi_head_attention(nn.Module):
    def __init__(self):
        super(Multi_head_attention, self).__init__()
        self.n_heads = n_heads
        self.w_q = nn.Linear(embedding_dimension, embedding_dimension*n_heads, bias=False)
        self.w_k = nn.Linear(embedding_dimension, embedding_dimension*n_heads, bias=False)
        self.w_v = nn.Linear(embedding_dimension, embedding_dimension*n_heads, bias=False)
        self.fc = nn.Linear( embedding_dimension*n_heads, embedding_dimension, bias=False)

    def forward(self, attr_q, attr_k, attr_v, attr_mask):
        '''
        attr_q, attr_k, attr_v: shape(batch_size, sequence_length, embedding_dim)
        attr_mask: shape(batch_size, sequence_length, sequence_length)

        q, k, v: shape(batch_size, n_heads, sequence_length, embedding_dim)
        attr_mask expend : shape(shape(batch_size, n_heads, seq_len, seq_len)

        context : shape(batch_size, n_heads, sequence_length, embedding_dim)
        context reshape: shape(batch_size, sequence_length, n_heads*embedding_dim)
        context fc: shape(batch_size, sequence_length, embedding_dim)
        '''
        batch_size = attr_q.shape[0]
        q = self.w_q(attr_q).view(attr_q.size(0), -1, self.n_heads, embedding_dimension).transpose(1, 2) 
        k = self.w_k(attr_k).view(attr_k.size(0), -1, self.n_heads, embedding_dimension).transpose(1, 2)
        v = self.w_v(attr_v).view(attr_v.size(0), -1, self.n_heads, embedding_dimension).transpose(1, 2)

        attr_mask = attr_mask.unsqueeze(1).repeat(1, self.n_heads, 1, 1)
        context = Attention()(q, k, v, attr_mask)
        context = context.transpose(1, 2).reshape(batch_size, -1, self.n_heads*embedding_dimension)
        context = self.fc(context)

        return nn.LayerNorm(embedding_dimension)(context + attr_q) #残差+layernorm

class feedforward(nn.Module):
    def __init__(self, ):
        '''
        构造两层linear，先升维，再降回原来维度，达到特征提取的效果
        '''
        super(feedforward, self).__init__()
        self.fc = nn.Sequential(
            nn.Linear(embedding_dimension, d_ff, bias=False),
            nn.ReLU(),
            nn.Linear(d_ff, embedding_dimension, bias=False)
        )
    def forward(self, x):
        output = self.fc(x)
        return nn.LayerNorm(embedding_dimension)(output+x)  #残差+layernorm

class Encode_layer(nn.Module):
    def __init__(self):
        super(Encode_layer, self).__init__()
        self.attention = Multi_head_attention()
        self.fc = feedforward()
    def forward(self, encode_inputs, mask):
        encode_output = self.attention(encode_inputs,encode_inputs, encode_inputs, mask)
        encode_output = self.fc(encode_output)
        return encode_output
```

#### 6.2.4 模型输出

输出为两个，1 是 NSP 任务的输出，2 是 MLM 任务的输出。

NSP 任务就是 1 取 [CLS] token 对应的输出，经过 linear 为 2 维。  
MLM 任务是取出 Encoder 输出中经过 mask 的 token 对应张量。

```
class Encode(nn.Module):
    def __init__(self):
        super(Encode, self).__init__()
        self.embedding = Embedding()
        self.layers = nn.ModuleList([Encode_layer() for _ in range(n_layers)])
        self.linear = nn.Sequential(nn.Linear(embedding_dimension, embedding_dimension),
                                   nn.Dropout(0.5),
                                   nn.Tanh(),
                                   nn.Linear(embedding_dimension, 2)) #是否连续的2分类问题

        self.linear2 = nn.Linear(embedding_dimension, embedding_dimension)
        self.gelu = gelu
        self.linear3 = nn.Linear(embedding_dimension, vocab_size, bias=False)
        self.linear3.weight = self.embedding.word_embedding.weight #权重用word embedding的权重


    def forward(self, input_ids, segment_ids, masked_pos):
        
        x = self.embedding(input_ids, segment_ids)
        pad_mask = self.padding_mask(input_ids, input_ids)
          
        #multi-head attention add+layernorm
        #feed-forward add+layernorm
        for layer in self.layers:
            x = layer(x, pad_mask) #x: shape[batch_size, max_sequence_length, embedding_dimension]
            
        #NSP任务输出 取[cls]位置输出
        nsp_output = self.linear(x[:, 0, :]) #shape(batch_size, 2)
        
        #MLM任务输出  需要在output(dim=1)max_sequence_length个张量中挑出max_num_mask个mask位置对应的张量
        masked_pos = masked_pos[:, :, None].expand(-1, -1, embedding_dimension) #shape(batch_size, max_sequence_length, embedding_dimension)
        masked_pos = torch.LongTensor(masked_pos.numpy())
        output = torch.gather(x, 1, masked_pos)#shape(batch_size, max_num_mask, embedding_dimension)
        output = self.gelu(self.linear2(output))
        mlm_output = self.linear3(output)

        return nsp_output, mlm_output


class BERT(nn.Module):
    def __init__(self):
        super(BERT, self).__init__()
        self.encode = Encode()
            
    def forward(self, input_ids, segment_ids, masked_pos):
        nsp_output, mlm_output = self.encode(input_ids, segment_ids, masked_pos)
        return nsp_output, mlm_output
```
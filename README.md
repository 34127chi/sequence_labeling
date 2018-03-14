序列标注 阅读笔记
====

综述
----
1，https://www.cnblogs.com/robert-dlut/p/6847401.html  中文综述  从传统的hmm、crf等到神经网络结构（先是基于NN/CNN-CRF模型，再后来主流是RNN-CRF模型，最近的研究是添加了attention机制以及少量标注训练数据进行的一些研究）觉得挺好的一篇博文<br/>

论文
----
1，Natural language processing (almost) from scratch  07年的一篇论文  详细了介绍了四种序列标注，提出了两种神经网络模型，是较早期用神经网络进行序列标注的工作之一  算得上神经网络运用在序列标注的入门论文 就是文章有点长<br/>
2，Bidirectional LSTM-CRF models for sequence tagging  RNN-CRF模型，考虑到rnn标注的时候只是当前最优，因此在后面一层crf，考虑加入了联合概率，优化的是整个序列（最终目标）<br/>
3，Attending to Characters in Neural Sequence Labeling Models 在2的基础上引入了字符特征，第一种方法是直接拼接在word特征后面，第二种方法是字符特征与word特征做加权<br>
4,Phonologically aware neural model for named entity recognition in low resource transfer settings 在原始BiLSTM-CRF模型上，加入了音韵特征，并在字符向量上使用attention机制来学习关注更有效的字符<br/>
5，Fast and Accurate Entity Recognition with Iterated Dilated Convolutions  idcnn + crf模型，里面比较有特点的是应用膨胀卷积做实体识别<br/>
6，Transfer Learning for Sequence Tagging with Hierarchical Recurrent Networks  提出了一种基于深层级循环神经网络和迁移学习的序列标注方法，该方法在源任务和目标任务之间共享隐藏特征表示和模型参数的一部分；并结合两项任务的目标函数，采用基于梯度的方法进行有效的训练；研究跨域，跨应用和跨语言迁移学习，并为每种情况提出一个共享框架图<br/>
7，Semi-supervised sequence tagging with bidirectional language models 该论文使用海量无标注语料库训练了一个双向神经网络语言模型，然后使用这个训练好的语言模型来获取当前要标注词的语言模型向量（LM embedding），然后将该向量作为特征加入到原始的双向RNN-CRF模型中，实验中是将词对应的LM embedding拼接到第一层lstm的结果中，论文作者也提到可以有不同的策略，例如对句子的LM embedding加入attention机制、在第二层lstm输入和第一层lstm结果之间加入非线性的变换<br/>

应用代码
----
1，https://github.com/crownpku/Information-Extraction-Chinese/tree/master/NER_IDCNN_CRF   有两个选项，其中一个是idcnn+crf，另一个是bilstm+crf<br/>

其他阅读
----
1，https://github.com/crownpku/Information-Extraction-Chinese/tree/master/RE_BGRU_2ATT   这个是选读的，关系抽取，也可以看看，用到了bilstm + 字级别的attention机制 以及 句子的attention机制<br/>
   ps：这个博主最近忙于为组织做贡献--中文文本标注工具，开源项目见：https://github.com/crownpku/Chinese-Annotator  用到了主动学习（active learning），该策略主要是用尽可能少量的标注数据来训练模型，起到减少人工标注成本，一般选取标注集的策略不同决定了算法的不同，以前看过主动学习相关的，但是一直没落地的产品，希望后期自己也能参与进来<br/>
2，attention机制的理解<br/>
    1，http://blog.csdn.net/malefactor/article/details/50550211  通俗地介绍了什么是attention，为什么用attention机制，从encode-decode这个框架阐述的，但没有对attention的种类进行不同角度的阐述<br/>
    2，http://blog.csdn.net/malefactor/article/details/50583474 是1的补充，对attention的机制类别进行了介绍，结合论文看更清楚<br/>
    3，Attention-Based Bidirectional Long Short-Term Memory Networks for Relation Classification（论文） 字级别的attention机制应用在关系提取中<br/>
    4，Neural Relation Extraction with Selective Attention over Instances（论文）  句子级别的attention机制应用在关系提取中<br/>

未完成任务
----
应用attention机制以及利用少量标注训练数据的序列标注文章还没看，所以未完待续。。。<br/>
   


# SequenceLabeling
序列标注

#综述
1，https://www.cnblogs.com/robert-dlut/p/6847401.html  中文综述  从传统的hmm、crf等到神经网络结构（先是基于NN/CNN-CRF模型，再后来主流是RNN-CRF模型，最近的研究是添加了attention机制以及少量标注训练数据进行的一些研究）觉得挺好的一篇博文

#论文：
1，Natural language processing (almost) from scratch  07年的一篇论文  详细了介绍了四种序列标注，提出了两种神经网络模型，是较早期用神经网络进行序列标注的工作之一  算得上神经网络运用在序列标注的入门论文 就是文章有点长
2，Bidirectional LSTM-CRF models for sequence tagging  RNN-CRF模型，考虑到rnn标注的时候只是当前最优，因此在后面一层crf，考虑加入了联合概率，优化的是整个序列（最终目标）
3，Fast and Accurate Entity Recognition with Iterated Dilated Convolutions  idcnn + crf模型，里面比较有特点的是应用膨胀卷积做实体识别

#应用代码：
1，https://github.com/crownpku/Information-Extraction-Chinese/tree/master/NER_IDCNN_CRF   有两个选项，其中一个是idcnn+crf，另一个是bilstm+crf

#其他阅读
1，https://github.com/crownpku/Information-Extraction-Chinese/tree/master/RE_BGRU_2ATT   这个是选读的，关系抽取，也可以看看，用到了bilstm + 字级别的attention机制 以及 句子的attention机制
   ps：这个博主最近忙于为组织做贡献--中文文本标注工具，开源项目见：https://github.com/crownpku/Chinese-Annotator  用到了主动学习（active learning），该策略主要是用尽可能少量的标注数据来训练模型，起到减少人工标注成本，一般选取标注集的策略不同决定了算法的不同，以前看过主动学习相关的，但是一直没落地的产品，希望后期自己也能参与进来
2，attention机制的理解
    1，http://blog.csdn.net/malefactor/article/details/50550211  通俗地介绍了什么是attention，为什么用attention机制，从encode-decode这个框架阐述的，但没有对attention的种类进行不同角度的阐述
    2，Attention-Based Bidirectional Long Short-Term Memory Networks for Relation Classification（论文） 字级别的attention机制应用在关系提取中
    3，Neural Relation Extraction with Selective Attention over Instances（论文）  句子级别的attention机制应用在关系提取中
    

应用attention机制以及利用少量标注训练数据的序列标注文章还没看，所以未完待续。。。
   


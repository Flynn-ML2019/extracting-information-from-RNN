# An implementation of extracting information from RNN

------

简介：该项目是在IMDB电影数据集上的二分类模型，主要功能如下：

1.实现了分类模型，该模型训练集的准确率为90%左右，测试集80%左右</br>
2.抽取每句话的Input Vector(维度:50),Hidden Vector(维度:10)和Output(维度:2)存为指定格式的文本文件</br>
3.用户可以自由指定相应的RNN模型，支持LSTM/GRU


## 运行环境及配置
> * 1.Python3
> * 2.Pytorch


## 代码文件说明
all.npy：存储好的IMDB电影数据集5W条(正[1,25000]/负[25000,50000]各2.5w条)</br>
wordVectors.npy：训练好的词向量，40w词，一个词50维</br>
word_to_index.txt：词嵌入中每个词的下标与词的对应关系，如 0->i,1->am,2->a,3->student...</br>
config.py：模型参数配置文件</br>
pytorch.py：模型主要实现</br>
tool.py：工具类</br>
model_pytorch_gru：GRU存储模型的目录</br>
model_pytorch_lstm：LSTM存储模型的目录</br>


## 实现流程
> * 对某个句子：如I am a student--(词嵌入)--->Input Vector---(抽取Hidden值)----->Result(Classification probability)


## 输出文件说明
```python
在项目目录下生成pytorch_input_hidden_result_lstm(或gru).txt
```


## 输出的文本内容格式说明

Sentence-[sentence-Index, word-Num]: I like playing football.</br>
True-Label:positive</br>
Predict-Label:positve</br>
Predict-Prob:[negative-0.3,positive-0.7]</br>
Word-[word-Index]-I: Embedding Input:[0.1,0.2,...,0.6]</br>
Word-[word-Index]-I: Hidden State:[0.2,0.6,...,0.8]</br>
Word-[word-Index]-I: Output :[0.3,0.7]</br>
...</br>
</br>
*******************************************************************</br>
Sentence-[sentence-Index, word-Num]:</br>
...</br>
...</br>
...</br>


## 程序运行相关的问题
Question:如何运行程序?</br>
Answer:pytorch.py是主文件，运行即可：python pytorch.py</br>

Question:我如何指定使用LSTM或是GRU?</br>
Answer:在config.py中修改model_used="gru"</br>

Question:我如何指定使用GRU?</br>
Answer:在config.py中修改use_gpu = True即可</br>

Question:我如何开始训练模型?</br>
Answer:在pytorch.py中打开#train()的注释并给test()加上注释，测试同理</br>

Question:有训练好的模型吗?</br>
Answer:有，提供一个GRU放在model_pytorch_gru下</br>


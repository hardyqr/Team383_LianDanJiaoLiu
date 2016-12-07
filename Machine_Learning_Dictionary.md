# Machine Learning Dictionary


### fine-tuning

>我们通过对ImageNet上训练出来的模型（如CaffeNet,VGGNet,ResNet)进行微调，然后应用到我们自己的数据集上。

fine-tuning:利用已有模型训练其他数据集:https://zhuanlan.zhihu.com/p/22624331<br>


>比如说，先设计出一个CNN结构。
>然后用一个大的数据集A，训练该CNN网络，得到网络a。
>可是在数据集B上，a网络预测效果并不理想（可能的原因是数据集A和B存在一些差异，比如数据来源不同导致的代表性差异）。如果直接用B的一部分训练的话，数据量太小，CNN不适用。
><br>
>解决方法：
>将数据集B分为train集和test，以a网络的参数为初始参数，以较小的学习率，以B的train集为训练数据，继续训练，得到网络b。
><br>
>这样，b在B的test集中一般可实现较好的预测精度。

https://www.zhihu.com/question/40850491/answer/88651844

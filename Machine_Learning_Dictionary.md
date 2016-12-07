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

### receptive field
>在卷积神经网络CNN中，决定某一层输出结果中一个元素所对应的输入层的区域大小，被称作感受野(receptive field)。
>举个例子，在maxpooling层中，如果它的kenerl size是2x2，输出结果中的每一个元素都是其对应输入的2x2的区域中的最大值，所以这一层的感受野大小就是2。
>其实感受野的大小是由kernel size和stride size一起决定的，公式是：rfsize = f(out, stride, ksize) = (out - 1) * stride + ksize，其中out是指上一层感受野的大小。

CNN中的感受野：https://zhuanlan.zhihu.com/p/22627224

### stride

>就是你每个convolution之间移动多少，这决定了你一层需要扫多少遍。直观理解就是每次观察局部和上一次重合度。所有CNN都这样理解stride。
https://www.zhihu.com/question/42047794

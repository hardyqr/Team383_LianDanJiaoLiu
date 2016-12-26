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


### GAN (aka Generative Adversarial Network)
Original paper: Generative Adversarial Nets:<br>
https://arxiv.org/pdf/1406.2661v1.pdf<br>
Invented by Ian Goodfellow<br>
<br>
What are the pros and cons of using generative adversarial networks?<br>
https://www.quora.com/What-are-the-pros-and-cons-of-using-generative-adversarial-networks-a-type-of-neural-network<br>
<br>
Improved Techniques for Training GANs:<br>
https://arxiv.org/pdf/1606.03498v1.pdf<br>
https://github.com/openai/improved-gan<br>
<br>
Application in Vision(end-to-end CNN):Deep Convolutional Generative Adversarial Networks(DCGAN):<br>
paper:https://arxiv.org/pdf/1511.06434v2.pdf<br>
code:https://github.com/Newmu/dcgan_code<br>
<br>
Why called generative&adversarial?
>The idea is to simultaneously train two neural nets. The first one, called **the Discriminator** — let’s denote it **D(Y)** — takes an input (e.g. an image) and outputs a scalar that **indicates whether the image Y looks “natural” or not**. In one instance of adversarial training, D(Y) can be seem as some sort of energy function that takes a low value (e.g. close to 0) when Y is a real sample (e.g. an image from a database) and a positive value when it is not (e.g. if it’s a noisy or strange looking image). The second network is called **the generator**, denoted **G(Z)**, where Z is generally a vector randomly sampled in a simple distribution (e.g. Gaussian). The role of the generator is to produce images so as to train the D(Y) function to take the right shape (low values for real images, higher values for everything else). During training D is shown a real image, and adjusts its parameter to make its output lower. Then D is shown an image produced from G and adjusts its parameters to make its output D(G(Z)) larger (following the gradient of some objective predefined function). But G(Z) will train itself to produce images so as to fool D into thinking they are real. It does this by getting the gradient of D with respect to Y for each sample it produces. In other words, it’s trying to minimize the output of D while D is trying to maximize it. Hence the name adversarial training.<br>

https://www.quora.com/What-are-some-recent-and-potentially-upcoming-breakthroughs-in-deep-learning<br>
<br>

>评价无监督学习好坏的方式有很多，其中生成任务就是最直接的一个。只有当我们能生成/创造我们的真实世界，才能说明我们是完完全全理解了它。（即generative models）<br>

近期GAN的模型和理论发展<br>
http://mp.weixin.qq.com/s?__biz=MzI1NTE4NTUwOQ==&mid=2650325352&idx=1&sn=90fb15cee44fa7175a804418259d352e&scene=0#wechat_redirect<br>
<br>
>“What I cannot create, I do not understand.” —Richard Feynman

Generative Models by OpenAI:<br>
https://openai.com/blog/generative-models/#contributions<br>



### Intersection Over Union (IoU)
分割结果与Ground Truth的交集比上它们的并集<br>
(Segmentation Result)∩(Ground Truth)/(Segmentation Result)∪(Ground Truth)
 
### Recall, Precesion and Accuracy
Differences among **Recall**, **Precision** and **Accuracy**: 

http://blog.csdn.net/pirage/article/details/9851339<br>
http://blog.csdn.net/wangran51/article/details/7579100<br>

假设原始样本中有两类，其中：<br>

1：假设类别1为正例，总共有 P个类别为1的样本。 <br>
2：假设类别0为负例，总共有N个类别为0的样本。 <br>


经过分类后：<br>

3：有TP个类别为1的样本被系统正确判定为类别1，FN个类别为1的样本被系统误判定为类别0，
显然有P=TP+FN。<br>
4：有FP个类别为0的样本被系统误判断定为类别1，TN个类别为0 的样本被系统正确判为类别0，
显然有N=FP+TN。

#### Precision  查准率
P = TP/(TP+FP)   

反映了**被分类器判定的正例**中**真正的正例**样本的比重

#### Recall  查全率
R = TP/(TP+FN) = 1 - FN/(TP+FN)   

反映了**被正确判定的正例**占**总的正例**的比重 


#### Accuracy
A = (TP + TN)/(P+N) = (TP + TN)/(TP + FN + FP + TN)      

反映了分类器统对整个样本的判定能力——能将正的判定为正，负的判定为负 


### F-Measure/F-Score  F1度量
http://blog.csdn.net/chjjunking/article/details/5933105<br>
http://blog.csdn.net/u011826404/article/details/53242081<br>
F-Measure是P和R的**加权调和平均**

#### 机器学习中的F1度量，为什么定义为precision和recall的调和平均，而不是算术平均？
>不懂理论，只凭经验说两句。抛砖引玉。
>假设p和r一个是1.0一个是0.1,算术平均会接近0.5 而调和平均接近0.2，这说明调和平均会强调两者的一致性，明显不一致时倾向于小的值，这更符合人们的直观感受。

https://www.zhihu.com/question/47980482


### Conditional Random Field (CRF)
[An Introduction to Conditional Random Fields](http://homepages.inf.ed.ac.uk/csutton/publications/crftut-fnt.pdf)<br>
[如何用简单易懂的例子解释条件随机场（CRF）模型？它和HMM有什么区别？](https://www.zhihu.com/question/35866596)<br>
[Efficient Inference in Fully Connected CRFs with Gaussian Edge Potentials](http://graphics.stanford.edu/projects/densecrf/densecrf.pdf)<br>
In segmentation problem, what its function is?<br>
DeepLab?<br>
context<br>
Anything else?


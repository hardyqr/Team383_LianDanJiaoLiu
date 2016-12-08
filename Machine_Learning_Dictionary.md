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

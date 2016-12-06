在做pixel-wise的预测时，一方面需要得到一个end-to-end的结果，另一方面由于卷积时stride的存在，会降低图片的size。
为了把卷积得到的feature map映射回一个和原图像size相同的矩阵，需要upsampling。<br> 

反卷积网络主要有1.unsupervised learning 2.visualize CNN 3. upsampling 三个功能。<br> 

https://www.zhihu.com/question/43609045/answer/132235276<br> 

<blockquote>
    <p>
（1）unsupervised learning，其实就是covolutional sparse coding[1][2]：这里的deconv只是观念上和传统的conv反向，传统的conv是从图片生成feature map，而deconv是用unsupervised的方法找到一组kernel和feature map，让它们重建图片。  <br> 
（2）CNN可视化[3]：通过deconv将CNN中conv得到的feature map还原到像素空间，以观察特定的feature map对哪些pattern的图片敏感，这里的deconv其实不是conv的可逆运算，只是conv的transpose，所以tensorflow里一般取名叫transpose_conv。  <br> 
（3）upsampling[4][5]：在pixel-wise prediction比如image segmentation[4]以及image generation[5]中，由于需要做原始图片尺寸空间的预测，而卷积由于stride往往会降低图片size， 所以往往需要通过upsampling的方法来还原到原始图片尺寸，deconv就充当了一个upsampling的角色。   <br> 


    </p>
</blockquote>

这里讨论反卷积在upsampling中的应用。也就是FCN[4]和DCAN[5]两篇文章。

<blockquote>
    <p>

分别简单介绍两篇文章，FCN和DCAN。FCN[4]主要用来做pixel-wise的image segmentation预测，先用传统的CNN结构得到feature map，同时将传统的full connected转换成了对应参数的卷积层，比如传统pool5层的尺寸是7×7×512，fc6的尺寸是4096，传统的full connected weight是7×7×512×4096这样多的参数，将它转成卷积核，kernel size为7×7，input channel为512，output channel为4096，则将传统的分别带有卷积和全连接的网络转成了全卷积网络(fully convolutional network, FCN)。FCN的一个好处是输入图片尺寸大小可以任意，不受传统网络全连接层尺寸限制，传统的方法还要用类似SPP结构来避免这个问题。FCN中为了得到pixel-wise的prediction，也要把feature map通过deconv转化到像素空间。论文中还有一些具体的feature融合，详情可参见论文。   <br> 
<br>
DCGAN[5]中使用deconv就更自然了，本身GAN就需要generative model，需要通过deconv从特定分布的输入数据中生成图片。GAN这种模式被Yann LeCun特别看好，认为是unsupervised learning的一个未来。   <br>  

    </p>
</blockquote>

[1] Zeiler M D, Krishnan D, Taylor G W, et al. Deconvolutional networks[C]. Computer Vision and Pattern Recognition, 2010. <br> 
[2] Zeiler M D, Taylor G W, Fergus R, et al. Adaptive deconvolutional networks for mid and high level feature learning[C]. International Conference on Computer Vision, 2011. <br> 
[3] Zeiler M D, Fergus R. Visualizing and Understanding Convolutional Networks[C]. European Conference on Computer Vision, 2013.   <br> 
[4] Long J, Shelhamer E, Darrell T, et al. Fully convolutional networks for semantic segmentation[C]. Computer Vision and Pattern Recognition, 2015.   <br> 
[5] Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks   <br> 
[6] Sparse Coding - Ufldl   <br> 
[7] Denoising Autoencoders (dA)   <br> 
[8] Convolution arithmetic tutorial 

# Image-to-Image Translation with Conditional Adversarial Networks

Paper:https://arxiv.org/pdf/1611.07004v1.pdf  
Project:https://phillipi.github.io/pix2pix/  
Code:https://github.com/phillipi/pix2pix  


## Method
#### GAN
>GANs are generative models that learn a mapping from random noise vector z to output image y.   

<br>
G:z->y<br>
<br>
#### cGAN
>Conditional GANs learn a mapping from observed image x and random noise vector z, to y.   

<br>
G:{x,z}->y
<br>

>The generator G is trained to produce outputs that cannot be distinguished from “real” images by an adversarially trained discrimintor, D, which is trained to do as well as possible at detecting the generator’s “fakes”.



### Network architectures
>We adapt our generator and discriminator architectures from those in DCGAN.

DCGAN:https://github.com/hardyqr/Team383_LianDanJiaoLiu/blob/master/DCGAN.md
>Both generator and discriminator use modules of the form convolution-BatchNorm-ReLu.   


Batch normalization: Accelerating deep network training by reducing internal covariate shift:
https://arxiv.org/pdf/1502.03167v3.pdf

Why Batch Normalization works?
https://www.zhihu.com/question/38102762


#### Generator with skips: U-Net
U-net: Convolutional networks for biomedical image segmentation:
https://arxiv.org/pdf/1505.04597.pdf


#### Markovian discriminator (PatchGAN)



### Model training
>we alternate between one gradient descent step on D, then one step on G.


# Deep Convolutional Generative Adversarial Network

Conference paper at ICLR 2016:<br>
Unsupervised Representation Learning With Deep Convolutional Generative Adversarial Networks<br>
https://arxiv.org/pdf/1511.06434v2.pdf<br>
Implementations:https://github.com/Newmu/dcgan_code<br>


## Model Architecture
>Core to our approach is adopting and modifying **three** recently demonstrated changes to CNN architectures.

<br>
### 1. All Convolutional Net
Springenberg et al., 2014<br>
>It replaces deterministic spatial pooling functions (such as maxpooling) with strided convolutions, 
>allowing the network to learn its own spatial downsampling. 
>We use this approach in our generator, allowing it to learn its own spatial upsampling, and discriminator.

### 2. Global Average Pooling instead of Fully Connected Layers
Mordvintsev et al.<br>
![No fully connected layers](https://github.com/hardyqr/Team383_LianDanJiaoLiu/blob/master/Images/Screen%20Shot%202016-12-08%20at%2017.59.37.png)
<br>
### 3.Batch Normalization
Ioffe & Szegedy, 2015<br>
>It stabilizes learning by **normalizing the input to each unit** to have **zero mean** and **unit variance**.

<br>
>Directly applying batchnorm to all layers however, resulted in sample oscillation and model instability. This was avoided by not applying batchnorm to the generator output layer and the discriminator input layer.

<br>
![CNN architecture summary](https://github.com/hardyqr/Team383_LianDanJiaoLiu/blob/master/Images/Screen%20Shot%202016-12-08%20at%2017.59.25.png)

##  Details of Adversarial Training
three datasets:<br>
Large-scale Scene Understanding (LSUN) (Yu et al., 2015)<br>
Imagenet-1k<br>
a newly assembled Faces dataset<br>
<br>
>All models were trained with mini-batch stochastic gradient descent (SGD) with a mini-batch size of 128.

<br>
>All weights were initialized from a zero-centered Normal distribution with standard deviation 0.02.

<br>
>In the LeakyReLU, the slope of the leak was set to 0.2 in all models.

<br>
>Adam optimizer (Kingma & Ba, 2014) with tuned hyperparameters.

<br>
>learning rate of 0.001 is too high, uisng 0.0002 instead.

<br>
>leaving the **momentum term** β_1 at the suggested value of 0.9 resulted in training oscillation(震荡) and instability while reducing it to 0.5 helped stabilize training.

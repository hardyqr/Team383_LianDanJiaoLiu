# Deep Convolutional Generative Adversarial Network

Conference paper at ICLR 2016:<br>
UNSUPERVISED REPRESENTATION LEARNING WITH DEEP CONVOLUTIONAL GENERATIVE ADVERSARIAL NETWORKS<br>
https://arxiv.org/pdf/1511.06434v2.pdf<br>
Implementations:https://github.com/Newmu/dcgan_code<br>

<br>
>Core to our approach is adopting and modifying **three** recently demonstrated changes to CNN architectures.

### 1. All Convolutional Net
Springenberg et al., 2014<br>
>It replaces deterministic spatial pooling functions (such as maxpooling) with strided convolutions, 
>allowing the network to learn its own spatial downsampling. 
>We use this approach in our generator, allowing it to learn its own spatial upsampling, and discriminator.

### 2. Global Average Pooling instead of Fully Connected Layers
Mordvintsev et al.<br>


### 3.Batch Normalization
Ioffe & Szegedy, 2015<br>
>It stabilizes learning by **normalizing the input to each unit** to have **zero mean** and **unit variance**.
<br>
>Directly applying batchnorm to all layers however, resulted in sample oscillation and model instability. This was avoided by not applying batchnorm to the generator output layer and the discriminator input layer.

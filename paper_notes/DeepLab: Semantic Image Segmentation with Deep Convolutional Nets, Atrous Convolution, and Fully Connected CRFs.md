# DeepLab: Semantic Image Segmentation with Deep Convolutional Nets, Atrous Convolution, and Fully Connected CRFs
paper:https://arxiv.org/pdf/1606.00915.pdf<br>
project:http://liangchiehchen.com/projects/DeepLab.html


>First, we highlight convolution with upsampled filters, or **‘atrous convolution’**, 
as a powerful tool in dense prediction tasks. Atrous convolution allows us to explicitly 
control the resolution at which feature responses are computed within Deep Convolutional
Neural Networks. It also allows us to effectively enlarge the field of view of filters 
to incorporate larger context without increasing the number of parameters or the amount
of computation. 

atrous convolution，一种upsampling filters，可增大filters的感知域而不增加参数和计算量。


>Second, we propose **atrous spatial pyramid pooling (ASPP)** to robustly segment objects 
at multiple scales. ASPP probes an incoming convolutional feature layer with filters at
multiple sampling rates and effective fields-of-views, thus capturing objects as well as 
image context at multiple scales. 


通过ASPP（一种pooling），多尺度，利用context。

>Third, we improve the localization of object boundaries by combining methods from DCNNs 
and probabilistic graphical models. The commonly deployed combination of max-pooling and
downsampling in DCNNs achieves invariance but has a toll on localization accuracy. 
We overcome this by combining the responses at the final DCNN layer with a fully connected 
Conditional Random Field (CRF), which is shown both qualitatively and quantitatively to 
improve localization performance.


DCNNs里的max-pooling+downsampling可以达成恒定性（？），但损失对边界的定位精度。最后加一个fully-connected 
Conditional Random Field就能提高定位精度。

Q：ASP Pooling以及atrous conv中的atrous和dilation conv有何异同？

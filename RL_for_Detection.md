# Reinforcement Learning for Object Detection
i.e. not using sliding window to obtain bounding boxes
## Active object localization with deep reinforcement learning


>In contrast to sliding windows, our approach does not follow a fixed path to search objects;
>instead, different objects in different scenes will end up in different search paths.


## Hierarchical Object Detection with Deep Reinforcement Learning 
NIPS 2016  
https://arxiv.org/pdf/1611.03718v2.pdf  



state=descriptor of the current region + memory vector<br>


These papers train an intelligent agent that, given an image window, 
is capable of deciding where to focus the attention among several 
different smaller region candidates. This top-down search is efficient 
to locate small objects in images but hard to apply to 3D data since 
a 3D scene can be extremely large and 3D objects’ sizes vary from class to class. 
	

# Test2_VOC_Faster-R-CNN
### 期中作业实验2（Faster R-CNN）
我们广泛认为：Faster R-CNN = RPN + Fast R-CNN  
##### Fast R-CNN:  
① 输入图像：输入一张待检测的图像；  
② 候选区域生成：使用Selective Search算法，在输入图像上生成~2K个候选区域；  
③ 特征提取：将整张图像传入CNN提取特征；  
④ 候选区域特征：利用RoIPooling分别生成每个候选区域的特征；  
⑤ 候选区域分类和回归：利用扣取的特征，对每个候选区域进行分类和回归。  
RoIPooling：利用特征采样，把不同空间大小的特征，变成空间大小一致的特征。  
将图像中ROI区域对应到卷积特征图中，将这个对应后的卷积特征区域通过池化操作固定到特定大小的特征，然后将特征送入全连接层。  
##### RPN:  
输入一张图像进入到VGG16网络中进行特征提取，得到Feature map，然后再Feature map上铺设上述的初始Anchors，这就是RPN的输入。  
RPN实际上有两个作用：  
①	对Anchors做二分类（前景，背景）  
②	对前景Anchors进行微调，把物体尽可能精确的框出来。  
由于Feature map上初始Anchors数量过多，所以我们对Anchors进行softmax二分类，得到前包含物体的概率和正负例Anchors。  
正例：对于所有Anchors与gt box的IOU大于阈值0.7的，我们认为是前景。  
负例：小于阈值0.3的则认为是背景。其他忽略。  
##### 实验参数设置：  
Faster-CNN实验中的详细参数设置：epoch与batch size分别为设为100与128，损失函数为交叉熵，激活函数为Relu，优化器为SGD，learning rate初始值为0.1。  
SSD实验中的详细参数设置：训练测试集划分是91分，主干网络vgg16，优化器是SGD，初始学习率2e-3，epoch100。



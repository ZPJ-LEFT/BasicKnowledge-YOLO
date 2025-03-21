# YOLO系列


## [YOLOv1](https://blog.csdn.net/weixin_43334693/article/details/129011644)

### 网络结构

- 输入：448*448
- 24个卷积层：将图像进行64倍下采样，提取出7*7（S×S个检测区域）的特征，维度1024
- 2个FC层：7*7*1024经过全连接输出为4096，再输出为1470=7*7*30

输出中，7*7是Grid Cell网络，30可以分为5+5+20，其中5是检测框(score,x,y,h,w)，20是20个类的概率

### 训练

- 预训练：先在ImageNet上进行分类任务的预训练，使用20个卷积+平均池化+全连接层
- 迁移学习：在预训练的前20层卷积后加入4层卷积+2层全连接，进行迁移学习
- 损失函数：坐标损失+置信度损失+分类损失

## [YOLOv2](https://zhuanlan.zhihu.com/p/432343631)

1. 添加Batch Norm层
2. 224*224预训练后，再进行448*448微调
3. 引入Anchor Box机制，输出k*(5+20)的输出结果
4. 使用全卷积神经网络
5. 新的主干网络DarkNet19
6. 基于Kmeans聚类算法自适应求解先验框
7. 使用PixelShuffle的逆操作Reorg，在不损失信息的情况下对图像下采样
8. 多尺度训练

## [YOLOv3](https://zhuanlan.zhihu.com/p/564855770)

1. 新的主干网络Darknet-53
2. 引入FPN
3. 利用logistic分类器取代Softmax，适应多标签分类
4. 分类损失使用binary cross-entropy loss

## [YOLOv4](https://blog.csdn.net/m0_57787115/article/details/130588237)

1. 输入：Mosaic数据增强、cmBN、SAT自对抗训练
1. 主干网络：CSPDarkNet53+Mish激活函数+DropBlock
2. Neck网络：SPP模块、FPN+PAN

# 面试经验

1. 介绍YOLO，并且解释一下为什么YOLO可以这么快？


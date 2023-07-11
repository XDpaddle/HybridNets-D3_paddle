# Hybridnets

**Hybridnets** Hybridnets是一个用于多任务的末端感知网络。我们的工作重点是交通目标检测、可行驶区域分割和车道检测。网络由backbone，neck与两个子检测head组成。


### 安装

- 安装paddle。
- 安装paddleseg，输入pip install paddleseg
- 进入工程文件根目录，输入pip install -r requirements.txt


### 测试
运行hybridnets_test.py。默认图片路径为demo\image。默认输出路径为demo_result。配置文件路径projects\bdd100k.yml


### 训练
设置train.py中is_train参数为False。运行train.py。如果想要重新开始训练或者接上一次的参数文件训练，应设置load_weights参数为None或checkpoints\bdd100k\参数文件名。训练集地址在配置文件中修改（路径project\bdd100k.yml）。
训练过程：通过设置freeze_seg,freeze_det,freeze_backbone参数冻结网络中各结构，训练时先冻结分割头训练一定回合，再冻结主干网络和检测头训练一定回合，最后全部解冻进行训练。

### 评估
设置train.py中is_train参数为True。

### 权重文件
权重文件可以从百度云中下载：https://pan.baidu.com/s/1VfsQ-XzXNHcDuAouyPBqog，提取码zo6w。测试图片与评估指标时分别将相应权重文件放在weights与checkpoints\bdd100k下，并修改测试代码中的load_weights参数使工程可以正确调用权重文件。（HybridNets-d3未采用预训练权重进行训练）。

## 参考：
本项目代码参考自：https://github.com/datvuthanh/HybridNets
paperwithcode：https://paperswithcode.com/paper/hybridnets-end-to-end-perception-network-1
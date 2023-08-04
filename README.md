# jittor-纺大人工智能小队-赛题一

| 第二届计图挑战赛开源竞赛
| 赛题一：风格及语义引导的风景图片生成赛题
｜展示方法的流程特点或者主要结果等

## 简介
| 简单介绍项目背景、项目特点

本项目包含了第二届计图挑战赛计图 - 草图生成风景比赛的代码实现。本项目的特点是：采用了guangan 方法对 图像 通过 风格及语义引导 处理，生成了 风景图片生成 的结果。

## 安装 
| 介绍基本的硬件需求、运行环境、依赖安装方法

本项目可在 4 张 Tesla V100 上运行，训练时间约为 52 小时。

#### 运行环境
- ubuntu 20.04 LTS
- python = 3.8.15
- jittor = 1.3.8.5

#### 安装依赖
执行以下命令安装 python 依赖
```
pip install -r requirements.txt
```

#### 预训练模型
预训练模型模型下载地址为 https:abc.def.gh，下载后放入目录 `<root>/weights/` 下。

## 训练
｜ 介绍模型训练的方法

## train.sh
CUDA_VISIBLE_DEVICES="0" python train.py --input_path {训练数据集路径（即train_resized文件夹所在路径）}


## 推理
｜ 介绍模型推理、测试、或者评估的方法

生成测试集上的结果可以运行以下命令：

此前需要：
将label与img的映射关系（label_to_img.json）放置在gaugan目录下

修改test.sh，其内容为：
CUDA_VISIBLE_DEVICES="0" python test.py  \
--input_path {测试数据集路径（即labels文件夹所在路径），它提供label mask图} \
--img_path {训练数据集的图片路径（即train_resized/imgs文件夹所在路径，它提供ref图）}
--which_epoch {使用的模型的epoch数目}

## 致谢

原作者将论文的 pytorch 版本的源代码，迁移到了 Jittor 框架当中。其中借鉴了开源社区 Spectral Normalization 的代码，以及重度参考了原论文的官方开源代码：SPADE。
此项目基于论文 *A Style-Based Generator Architecture for Generative Adversarial Networks* 实现，部分代码参考了 [jittor-gan](https://github.com/Jittor/gan-jittor)。

## 注意事项

点击项目的“设置”，在Description一栏中添加项目描述，需要包含“jittor”字样。同时在Topics中需要添加jittor。

![image-20220419164035639](https://s3.bmp.ovh/imgs/2022/04/19/6a3aa627eab5f159.png)

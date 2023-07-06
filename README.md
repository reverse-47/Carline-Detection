# Carline-Detection
本项目基于2022年发布的A Keypoint-based Global Association Network for Lane Detection.对原作者的GANet模型进行了修改，使之适用于cpu环境，再进行模型的训练和测试。最后移植至开发板，完成实地测试。

项目原型论文：https://arxiv.org/abs/2204.07335

项目原型代码仓库地址：https://github.com/Wolfwjs/GANet

原作者的GANet模型：

![image](https://github.com/reverse-47/Carline-Detection/assets/85037574/e52fef24-25ab-4d71-b956-8243923fd325)

我们基于以上的模型进行了如下步骤：

1.修改模型中的LFA中的可变形卷积层，使其可以适用于CPU环境

2.修改测试文件中的与gpu相关的参数，改为cpu

3.替换输入与输出方式，移植至开发板

## 移植步骤
我们选择的是华为晟腾的Atlas 200 Developer Kit 开发板，搭载树莓派V2.1相机。

1.参照Atlas 200DK官方文档对开发板进行操作系统烧录

2.配置OS依赖及python环境

3.移植代码

4.参照CANN中调用相机步骤，替换原测试文件中的图片读取输入为相机拍摄输入

5.通过Websocket将推理生成的图片展示至网页页面，实时传输，实时读取

## 快速上手
快速运行本项目（开发板端），请按照以下步骤执行：

1.按照移植步骤中的1、2配置好Atlas 200DK的项目运行环境

2.配置项目的python依赖
```shell
pip install pytorch==1.6.0 torchvision==0.7.0 -c pytorch -y
pip install -r requirements/build.txt
```
2.运行如下代码：
```shell
git clone https://github.com/reverse-47/Carline-Detection.git
cd Code/GANet
python setup.py
cd tools
python ganet/culane/test_dataset.py ../configs/culane/final_exp_res18_s8.py [模型文件]
```
## 运行效果

![image](https://github.com/reverse-47/Carline-Detection/assets/85037574/31ac6893-be13-4f06-9603-4bf01083a02b)

以上为测试集推理结果

![image](https://github.com/reverse-47/Carline-Detection/assets/85037574/ea0d68eb-a0d8-4160-8514-c31115a5afe3)

以上为实地测试中相机拍摄输入图像推理结果

模型文件请联系3375939661@qq.com获取

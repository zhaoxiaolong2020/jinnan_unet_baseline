# Unet Baseline
XuYuan 大哥的Unet做到了top-1,我这个就抛砖引玉了。

## 依赖项
- *Python3*
- *Pytorch 0.4 或者更高*
- *cv2*
- *coco API*

## 模型训练
请先确保/mnt/目录下有文件夹jinnan2_round2_train_20190401或者修改config下的目录。
```
python train_se50.py
python train_se101.py
```
两个模型训练大概30~40小时。
不断从小尺度finetune能加快训练速度(我这里给的脚本不是这样的)。我们线下是这样训练的256->512->768。

## 模型测试
参考 ```test_round2_b.py```
线下验证参考```val.py```

## 模型线下验证结果
这是我们线上比赛模型的精度。如果有大佬训练的模型能够超过这个精度的话希望能和我分享一下。

| Model             |  img_size   |  mIoU.      | TTA6  mIoU. |
| ------------------| ----------- | ----------- |------------ |
| Se-ResNext101     |  768*768    |  78.082     |    78.764   |
| Se-ResNext50      |  960*960    |  78.30      |    78.45    |
| model-ensemble    |             |  78.782     |    79.153   |

## 硬件平台
* 阿里云服务器 P100 16G显存
* 线下测试1080ti 11G显存

## 训练的一些问题
* batch size 对训练精度有一定影响
* 增大图片尺寸和多尺度训练都没有做（时间不够）有实验条件的可以试试

## 如果你认真看了代码还有问题的话
wechat: nn19950720

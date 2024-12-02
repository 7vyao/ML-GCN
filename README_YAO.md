# **因为pytorch、numpy版本不同代码不适用问题，对coco、util、engine、models四个文件的部分代码进行修改**

**## 详细修改**

1. 对coco文件中自动下载数据集部分进行注释，手动下载数据集，数据集保存目录为 ' ./data/coco '
2. coco文件138行，数据集路径从自动下载目录 ' ./data/coco/data ' 更改为手动下载 './data/coco '
3. engine文件83行， .data[0]（在pytorch0.4版本后被弃用）更改为 .item()
4. models文件95行，pretrained（在pytorch1.13版本后被弃用）更改为weights，且ResNet101 的预训练权重可以使用 ResNet101_Weights.IMAGENET1K_V1（models）
5. util文件301行，np.int（在numpy1.20版本后被弃用）更改为python内置的int

## **补充修改**

1. models文件“gcn_resnet101”函数，初始化模型权重加入“checkpoint_path”参数，使用预训练过的模型权重
2. demo_coco_gcn.py文件51行，加入预训练模型权重

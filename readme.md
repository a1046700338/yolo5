<div>
   <a href="https://github.com/ultralytics/yolov5/actions/workflows/ci-testing.yml"><img src="https://github.com/ultralytics/yolov5/actions/workflows/ci-testing.yml/badge.svg" alt="CI CPU testing"></a>
   <a href="https://zenodo.org/badge/latestdoi/264818686"><img src="https://zenodo.org/badge/264818686.svg" alt="YOLOv5 Citation"></a>
   <a href="https://hub.docker.com/r/ultralytics/yolov5"><img src="https://img.shields.io/docker/pulls/ultralytics/yolov5?logo=docker" alt="Docker Pulls"></a>
   <br>
   <a href="https://colab.research.google.com/github/ultralytics/yolov5/blob/master/tutorial.ipynb"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"></a>
   <a href="https://www.kaggle.com/ultralytics/yolov5"><img src="https://kaggle.com/static/images/open-in-kaggle.svg" alt="Open In Kaggle"></a>
   <a href="https://join.slack.com/t/ultralytics/shared_invite/zt-w29ei8bp-jczz7QYUmDtgo6r6KcMIAg"><img src="https://img.shields.io/badge/Slack-Join_Forum-blue.svg?logo=slack" alt="Join Forum"></a>
</div>

# yolov5
YOLOv5🚀是一个在COCO数据集上预训练的物体检测架构和模型系列，它代表了Ultralytics对未来视觉AI方法的公开研究，其中包含了在数千小时的研究和开发中所获得的经验和最佳实践。

# 准备
## 使用yolo前需要配置的环境
 1. 安装[Anconda](https://www.anaconda.com/products/distribution#Downloads)
 2. Anconda 虚拟环境添加新路径 
`conda config --add envs_dirs 你的envs路径`
 3. Anconda 清华源配置  
```shell
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
conda config --set show_channel_urls yes
```
若安装paddle出错，可以修改镜像源
```shell
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/free/
conda config --set show_channel_urls yes
```
 4. 创建yolo虚拟空间
 ```shell
 conda create -n 命名 python=选择合适的python版本
 ```
 像这样
 ```shell
 conda create -n yolo python=3.8
 ```
 5. 进入yolo虚拟空间
 ```shell
 conda activate yolo
 ```
 6. git yolo仓库，我用的yolo版本是v5
 选择合适的目录（不要有中文命名的目录)打开cmd
 ```shell
 git clone git@git.zhlh6.cn:ultralytics/yolov5.git
 ```
 使用了加速源下载，放心下载不会慢
 7. 进入下载好的yolo目录，下载依赖
 ```shell
 pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
 ```
 如果要使用wandb，还要下载一个 wandb
 ```shell
 pip install wandb -i https://pypi.tuna.tsinghua.edu.cn/simple
 ```
 8. 数据标注
 使用[labelimg](https://github.com/heartexlabs/labelImg)进行数据标注  
 也可以直接下载数据集，这个数据集网站非常好用，[链接](https://roboflow.com/)  
 进入yolo虚拟空间中，下载labelimg
 ```shell
 pip install labelimg -i https://pypi.tuna.tsinghua.edu.cn/simple
 ```

# 使用
## 使用本项目
[项目地址](https://github.com/a1046700338/yolo5) | [Gitee](https://gitee.com/sakurafeiyu/yolo5)  

## git clone仓库到本地
`git clone git@git.zhlh6.cn:a1046700338/yolo5.git` or `git clone https://github.com/a1046700338/yolo5.git`

## 使用PyCharm打开yolo项目
File -> Settings -> Project:yolov5 -> Python Interpreter -> add -> Conda Enviroment -> Existing Enviroment -> 选择你的虚拟环境路径 -> ok  

运行代码测试 train.py

## 添加你的数据集
将你的数据集文件复制到项目根目录下，并在 `data` 目录下创建一个yaml文件，自行命名，  
yaml文件内容：
```
train: ../train/images #你的数据集路径
val: ../valid/images	#你的有效集路径

nc: 2	#你的classes数量
names: ['mask', 'no-mask'] #数组内是你的classes，标签
```

之后修改 `train.py` 第460行代码，即可
```yaml
    parser.add_argument('--data', type=str, default='data/文件名.yaml', help='data.yaml path')
```

# 运行
所有环境配置好后，运行 `train.py` 

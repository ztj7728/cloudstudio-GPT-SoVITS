# cloudstudio-GPT-SoVITS

使用Pytorch2.0.0模板启动高性能实例

# 安装git-lfs

apt update
apt install git-lfs

# 使用conda境内加速源（https://help.mirrors.cernet.edu.cn/anaconda/）
vi ~/.condarc

#替换为以下信息
channels:
  - defaults
show_channel_urls: true
default_channels:
  - https://mirrors.sustech.edu.cn/anaconda/pkgs/main
  - https://mirrors.sustech.edu.cn/anaconda/pkgs/r
  - https://mirrors.sustech.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: https://mirrors.sustech.edu.cn/anaconda/cloud
  pytorch: https://mirrors.sustech.edu.cn/anaconda/cloud
  nvidia: https://mirrors.cernet.edu.cn/anaconda-extra/cloud

# 更新conda
conda install -n base -c conda-forge conda=25.3.1

# 创建GPTSoVits的conda环境
conda create -n GPTSoVits python=3.9
conda activate GPTSoVits
# 先安装降级的mkl
conda install mkl=2021.4.0 mkl-service=2.4.0

# 拉取仓库
git clone https://github.com/RVC-Boss/GPT-SoVITS.git

# 安装

cd GPT-SoVITS

bash install.sh

# 拉取大模型
cd GPT-SoVITS
rm -r pretrained_models #删除原目录
git clone https://hf-mirror.com/lj1995/GPT-SoVITS
mv GPT-SoVITS pretrained_models #修改GPT-SoVITS目录名为大模型目录命

#返回项目运行webui或者api
cd /workspace/GPT-SoVITS
python webui.py



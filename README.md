帮助在linux段完全跑通3dgs流程，代码放在了master分支下

将所有文件上传到linux平台，创建虚拟环境

conda create -n guassian python=3.10.13

conda activate guassian

安装pytorch，要选择适配自己cuda的版本，例如我的是cuda12.1

conda install pytorch==2.4.0 torchvision==0.19.0 torchaudio==2.4.0 pytorch-cuda=12.1 -c pytorch -c nvidia

环境配置后，可以进行预编译

cd submodules/diff-gaussian-rasterization

python setup.py install

cd submodules/simple-knn

python setup.py install

cd submodules/fused-ssim

python setup.py install

安装工具包

pip install plyfile tqdm opencv-python-headless joblib


在主目录下创建data/input,在input内放准备好的数据集，随后调用colmap生成点云文件

python convert.py -s data 

最后调用主程序训练数据集

python train.py -s data

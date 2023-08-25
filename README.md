# detect_trash_by_yolox
detect trash AI by yolox on jetson nano

#スワップメモリの設定

## make swapfile
$ sudo dd if=/dev/zero of=/var/swapfile bs=1G count=4
## initialize swapfile
$ sudo mkswap /var/swapfile
$ sudo chmod 600 /var/swapfile
## mount swap when Jetson run.write in last row
$ sudo vi /etc/fstab
"/var/swapfile          none        swap          swap       0 0"

## activate swapfile
$ sudo swap on /var/swapfile
## confirm swap
$ free -m
$ swap on -s

## jtopのインストール
$ sudo apt install python-pip
$ sudo -H pip install -U jetson-stats
$ sudo reboot
## jtop run
$ jtop

## install termal monitor
$ sudo apt install python3-pip
$ sudo apt install libfreetype6-dev
$ sudo apt install python3-numpy
$ sudo apt install python3-matplotlib
# download Jetson-thermal-monitor tool from GitHub
$ git clone https://github.com/tsutof/jetson-thermal-monitor
# run tool
$ cd jetson-thermal-monitor
$ python3 jetson-temp-monitor.py

NVIDIA NGC L4T ML
https://catalog.ngc.nvidia.com/orgs/nvidia/containers/l4t-ml
JetPack 4.6.1 (L4T R32.7.1)

l4t-ml:r32.7.1-py3
TensorFlow 1.15.5
PyTorch v1.10.0
torchvision v0.11.0
torchaudio v0.10.0
onnx 1.11.0
CuPy 9.2.0
numpy 1.19.5
numba 0.53.1
OpenCV 4.5.0 (with CUDA)
pandas 1.1.5
scipy 1.5.4
scikit-learn 0.24.2
JupyterLab 2.2.9

Jetpack 4.5の時、l4t-ml:r32.5.0-py3
dockerファイルをpull
$ sudo docker pull nvcr.io/nvidia/l4t-ml:r35.2.1-py3
Docker ファイルをrun
$ sudo docker run -it --rm --runtime nvidia --network host nvcr.io/nvidia/l4t-ml:r32.7.1-py3
#Dockerにボリュームを構築する。
$ docker volume create test_volume
$ docker volume ls
#Dockerをボリュームをマウントして、起動する。
$ docker run -it --name l4t-ml_vol --mount type=volume,src=test_volume,target=/home --runtime nvidia --network host nvcr.io/nvidia/l4t-ml:r32.7.1-py3


$ apt-get update

$ apt-get install vim 

# -*- coding:utf-8 -*-を最初に入れる。

$ sudo apt install python3-pip

$ pip3 install xmltodict

$ pip3 install keras==2.2.4

$ pip3 install tqdm==4.11.2

## 文字化けは以下のコマンドをdocker で入力する。
$ export LANG=C.UTF-8
$ export LANGUAGE=en_US:

## convert_coco_to_voc.pyのfilenameからsplitを取り除く。
## Workフォルダを作成して、作業はその中でのみ行う。
$ mkdir ~/work



### Deviceにラズパイカメラを起動時に入れる必要あり？


## convert_coco_to_vocの198行目を'filename':filenameに変更する。
## voc_annotation.pyのイカを変える。
## 123行目をimage_pathに帰る。
## 以下のコマンドで拡張子JPGをjpgに変更する。
$ find /path/to/your/folder/ -type f -name "*.JPG" -exec sh -c 'mv "$0" "${0%.JPG}.jpg"' {} \;

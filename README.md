# ubuntu-software

## mirrors.tuna

```bash
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo rm /etc/apt/sources.list
sudo vim /etc/apt/sources.list
```

```txt
# 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
```

```bash
sudo apt-get update
```

## apt-get

```bash
sudo apt-get install vim

sudo add-apt-repository ppa:graphics-drivers/ppa

sudo add-apt-repository ppa:apt-fast/stable
sudo apt-get install apt-fast

sudo add-apt-repository ppa:fossfreedom/indicator-sysmonitor
sudo apt-get install indicator-sysmonitor

sudo apt-fast install zsh curl git ssh net-tools make gcc libglib2.0-dev libsm-dev libxrender-dev exfat-utils screen htop
sudo chsh -s /bin/zsh
reboot

```

## oh-my-zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
git clone git://github.com/zsh-users/zsh-syntax-highlighting $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
sudo apt-get install autojump
```

```bash
sudo vim ~/.zshrc
# update such as:
# plugins=(git zsh-autosuggestions zsh-syntax-highlighting web-search extract autojump)
source ~/.zshrc
```

### Ubuntu terminal zsh agnoster theme garbled

[Ubuntu 终端zsh的agnoster主题乱码](https://blog.csdn.net/CoderMannul/article/details/90724645)

```bash
wget https://raw.githubusercontent.com/powerline/powerline/develop/font/10-powerline-symbols.conf
wget https://raw.githubusercontent.com/powerline/powerline/develop/font/PowerlineSymbols.otf
sudo mkdir /usr/share/fonts/OTF
sudo cp 10-powerline-symbols.conf /usr/share/fonts/OTF/
sudo mv 10-powerline-symbols.conf /etc/fonts/conf.d/
sudo mv PowerlineSymbols.otf /usr/share/fonts/OTF/
```

## python

### Miniconda

if use zsh, copy conda's initialize from .bashrc to .zshrc

```bash
vim ~/.zshrc
```

```txt
# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$('/root/miniconda3/bin/conda' 'shell.bash' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "/root/miniconda3/etc/profile.d/conda.sh" ]; then
        . "/root/miniconda3/etc/profile.d/conda.sh"
    else
        export PATH="/root/miniconda3/bin:$PATH"
    fi
fi
unset __conda_setup
# <<< conda initialize <<<
```

### conda source

[use 清华源 to accurate download](https://mirror.tuna.tsinghua.edu.cn/help/anaconda/)

### pip source

清华源

```bash
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```

豆瓣源

```bash
pip config set global.index-url https://pypi.doubanio.com/simple
```

### pytorch 1.3

if use cuda10.0 and pytorch 1.3

```bash
pip install torch==1.3.0+cu100 torchvision==0.4.1+cu100 -f https://download.pytorch.org/whl/torch_stable.html
```

if use cuda10.1 and pytorch 1.3

```bash
pip install torch===1.3.0 torchvision===0.4.1 -f https://download.pytorch.org/whl/torch_stable.html
```

### apex

```bash
git clone https://github.com/NVIDIA/apex
cd apex
pip install -v --no-cache-dir --global-option="--cpp_ext" --global-option="--cuda_ext" ./
cd ..
rm -r apex
```

### gdal

```bash
conda install gdal --yes
```

### other package

```bash
pip install -r requirments.txt
```

### jupyter lab

```bash
conda install -c conda-forge jupyterlab
```

```bash
ipython
```

```python
from notebook.auth import passwd
passwd()
exit()
```

```bash
jupyter lab --generate-config
vim ~/.jupyter/jupyter_notebook_config.py

```

```python
c.NotebookApp.ip = '*'
c.NotebookApp.password = 'sha1:***'
c.NotebookApp.open_browser = False
c.NotebookApp.port = 8888
c.NotebookApp.allow_remote_access = True
```

start

```bash
jupyter lab
```

## cuda

if cuda has installed.

```bash
 sudo vim /etc/profile
 ```

 ```txt
export PATH=/usr/local/cuda/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH
export CUDA_HOME=/usr/local/cuda
 ```

## ss

```bash
sudo apt-add-repository ppa:hzwhuang/ss-qt5
sudo apt-fast update
sudo apt-fast install shadowsocks-qt5s
```

## screen shot

ubuntu18.04

```bash
sudo apt-fast install flameshot
```

ubuntu16.04

```bash
sudo apt install g++ build-essential qt5-default qt5-qmake qttools5-dev-tools
sudo apt install libqt5dbus5 libqt5network5 libqt5core5a libqt5widgets5 libqt5gui5 libqt5svg5-dev
sudo apt install git openssl ca-certificates
git clone https://github.com/lupoDharkael/flameshot.git
cd flameshot
mkdir build
cd build
qmake ../
sudo make
sudo make install
flameshot gui
```

## download

```bash
sudo add-apt-repository ppa:plushuang-tw/uget-stable
sudo apt-fast install uget
sudo apt-fast install aria2
```

编辑”->“设置（S）……”，在弹出的界面中选择“插件”  选择插件匹配顺序“aria2”

## pycharm

if there isn't a desktop icon

```bash
sudo gedit /usr/share/applications/Pycharm.desktop
```

The following path should base on the actual path.

```txt
[Desktop Entry]
Type=Application
Name=Pycharm
GenericName=Pycharm3
Comment=Pycharm3:The Python IDE
Exec=sh /home/arron/pycharm-community-2018.2.2/bin/pycharm.sh
Icon=/home/arron/pycharm-community-2018.2.2/bin/pycharm.png
Terminal=pycharm
Categories=Pycharm
```

## docker

### build docker image

```bash
sudo docker pull nvidia/cuda:10.1-cudnn7-runtime-ubuntu18.04
```

### docker-nvidia

```bash
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt-get update && sudo apt-get install -y nvidia-container-toolkit
sudo systemctl restart docker
```

### docker run

```bash
sudo docker run -d -it  -v /home/arron/:/home/arron/ --gpus 1 --name deeplearning nvidia/cuda:10.1-cudnn7-runtime-ubuntu18.04
```

### enter contatiners

```bash
sudo docker exec -it deeplearning bash
nvidia-smi
cat /usr/local/cuda/version.txt
```

### rm all

```bash
sudo docker stop $(docker ps) & docker rm $(docker ps -aq)
```

### save docker images

```bash
sudo docker commit containerId arron/deeplearning
sudo docker save -o 10.1-cudnn7-runtime-ubuntu18.04-pytorch1.3-tensorflow2.0.tar arron/deeplearning
```

## others

- pycharm
- vscode
- sogou
- teamviewer

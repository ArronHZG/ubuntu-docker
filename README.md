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
sudo apt-get install vim software-properties-common

sudo add-apt-repository ppa:graphics-drivers/ppa

sudo add-apt-repository ppa:apt-fast/stable
sudo apt-get install apt-fast

sudo add-apt-repository ppa:fossfreedom/indicator-sysmonitor
sudo apt-get install indicator-sysmonitor

sudo apt-fast install zsh curl git ssh net-tools iputils-ping make gcc libglib2.0-dev libsm-dev libxrender-dev exfat-utils
sudo apt-fast install screen htop zip unzip rar unrar rename lightdm
sudo chsh -s /bin/zsh
reboot

```

## oh-my-zsh

```bash
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O - --no-check-certificate)"
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

### theme

https://github.com/ohmyzsh/ohmyzsh/wiki/Themes

推荐
theunraveler af-magic ys pure avit bira 

### Ubuntu terminal zsh agnoster theme garbled agnoster

[Ubuntu 终端zsh的agnoster主题乱码](https://blog.csdn.net/CoderMannul/article/details/90724645)

```bash
wget https://raw.githubusercontent.com/powerline/powerline/develop/font/10-powerline-symbols.conf
wget https://raw.githubusercontent.com/powerline/powerline/develop/font/PowerlineSymbols.otf
sudo mkdir /usr/share/fonts/OTF
sudo cp 10-powerline-symbols.conf /usr/share/fonts/OTF/
sudo mv 10-powerline-symbols.conf /etc/fonts/conf.d/
sudo mv PowerlineSymbols.otf /usr/share/fonts/OTF/
```

在docker中
(anon):12: character not in range
.zshrc 和 .bashrc 文件底部添加以下两行：
```bash
export LC_ALL=C.UTF-8
export LANG=C.UTF-8
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

#### conda source

[use 清华源 to accurate download](https://mirror.tuna.tsinghua.edu.cn/help/anaconda/)

#### base
if you don't want to see (base)  on terminal:
```txt
# add in ~/.condarc
changeps1: false

```
### pip

清华源

```bash
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```

豆瓣源

```bash
pip config set global.index-url https://pypi.doubanio.com/simple
```

### pytorch 1.6

cuda10.2 and pytorch 1.6

```bash
pip install torch==1.6.0+cu102 torchvision==0.7.0+cu102 -f https://download.pytorch.org/whl/torch_stable.html
```

### apex

```bash
git clone https://github.com/NVIDIA/apex
cd apex
pip install -v --no-cache-dir --global-option="--cpp_ext" --global-option="--cuda_ext" ./
cd ..
rm -r apex
```

error:

    FileNotFoundError: [Errno 2] No such file or directory: '/usr/local/cuda/bin/nvcc': '/usr/local/cuda/bin/nvcc'



### conda package

```bash
conda install --yes --file conda_requirements.txt
```

### other package

```bash
pip install -r requirements.txt
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

# nvidia driver

remove nouveau and reboot
```
sudo apt-get --purge remove xserver-xorg-video-nouveau
sudo apt-get --purge remove gvfs-daemons
sudo apt-get --purge remove libdrm-nouveau2/now
sudo reboot
```

download nvidia driver
```
sudo bash NVIDIA-Linux-x86_64-440.100.run
```

## cuda

download cuda


```
sudo bash cuda_10.2.89_440.33.01_linux.run
sudo bash cuda_10.2.1_linux.run
```

if cuda has installed, some path should be exported.

```bash
 sudo vim /etc/profile
 ```

 ```txt
export PATH=/usr/local/cuda/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH
export CUDA_HOME=/usr/local/cuda
 ```
 
 ```bash
 source /etc/profile
 zsh
 ```
 
 test
 ```
 nvcc -V
 ```
 
 ## cudnn
 
 download cudnn
 ```
 sudo dpkg -i libcudnn8_8.0.3.33-1+cuda10.2_amd64.deb
 ```

## ss

```bash
sudo apt-add-repository ppa:hzwhuang/ss-qt5
'''

In ubuntu18 ,there will be some error:

```txt
E: The repository 'http://ppa.launchpad.net/hzwhuang/ss-qt5/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

fix:
```
cd /etc/apt/sources.list.d
sudo vim hzwhuang-ubuntu-ss-qt5-bionic.list
# change bionic to xenial
sudo apt-get update
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

### download docker for ubuntu

https://docs.docker.com/engine/install/ubuntu/


### docker 不需要sudo 权限

```

sudo groupadd docker
sudo gpasswd -a <你的用户名> docker
sudo service docker restart
```

重开shell

### build docker image

```bash
sudo docker pull nvidia/cuda:10.0-cudnn7-devel-ubuntu18.04
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
sudo docker run -d -it  -v /home/:/home/  -v /mnt/:/mnt/ -p 8022:22  --shm-size=2G --gpus 1 --name cuda10-devel nvidia/cuda:10.0-cudnn7-devel-ubuntu18.04

# --runtime=nvidia
```

### enter contatiners

```bash
sudo docker exec -it cuda10-devel bash
nvidia-smi
nvcc -V
cat /usr/local/cuda/version.txt
```

### contatiner ssh


```
vim vi /etc/ssh/sshd_config

UsePAM no #取消pam登录限制
PubkeyAuthentication yes #启用公钥私钥配对认证方式
AuthorizedKeysFile .ssh/authorized_keys #公钥文件路径（和上面生成的文件同）
PermitRootLogin yes #root能使用ssh登录 , 需要使用 passwd 给容器设置密码
```

'''
service ssh restart
```

将远程访问公钥写入authorized_keys之中, 方法见[ssh](## ssh)

### rm all

```bash
sudo docker stop $(docker ps) & docker rm $(docker ps -aq)
```

### save docker images


```bash
sudo docker rmi arron/10.0-cudnn7-devel-ubuntu18.04
docker commit -a "arron" -m "cuda10 torch1.3.0" [containerId]  arron/cuda10:torch1.3.0
sudo docker save -o arron-10.0-cudnn7-devel-ubuntu18.04.tar arron/10.0-cudnn7-devel-ubuntu18.04
```

## others

- pycharm
- vscode
- sogou
- teamviewer

## ssh

A/B host computer
```bash
ssh-keygen
```

A host computer

```bash
scp ~/.ssh/id_rsa.pub  arron@10.103.xxx.xxx:/home/arron
```

B host computer

```bash
cat id_rsa.pub >> ~/.ssh/authorized_keys 
```


or use A computer
```
ssh-copy-id -i ~/.ssh/id_rsa.pub arron@10.103.xxx.xxx
```
## samba
本地使用图像化界面远程访问服务器文件
```shell
sudo apt-get install samba
```
默认配置为每个用户可以访问到home下自己的文件夹

[ubuntu下的Samba配置：使每个用户可以用自己的用户名和密码登录自己的home目录](https://blog.csdn.net/fly_qj/article/details/21744797)
```shell
sudo vim /etc/samba/smb.conf
```
修改内容:
找到[homes]项，此项默认是注释掉的，取消其注释，然后修改其具体内容，修改成如下：
```
[homes]
   comment = Home Directories
   browseable = yes
   read only = no
   create mask = 0755
   directory mask = 0755
   valid users = %S
```
重启 samba
```
sudo service smbd restart
sudo service nmbd restart
```

给现有用户开通samba 权限
```
sudo smbpasswd -a [用户名] # 用户密码独立设置
```

其他配置参考
https://www.cnblogs.com/kevingrace/p/8662088.html

##
修改键位
美化桌面
```shell
sudo apt install gnome-tweak-tool
```
ubuntu 触摸板增强
```shell
sudo apt-get install fusuma
```
ubuntu 剪切版历史记录
```
sudo apt-get install  parcellite
```

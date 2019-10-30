# build docker image
```
sudo docker pull nvidia/cuda:10.1-cudnn7-runtime-ubuntu18.04
```

# docker-nvidia
```
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt-get update && sudo apt-get install -y nvidia-container-toolkit
sudo systemctl restart docker
```


# docker run
```
sudo docker run -d -it  -v /home/arron/:/home/arron/ --gpus 1 --name deeplearning nvidia/cuda:10.1-cudnn7-runtime-ubuntu18.04
```

# enter contatiners
```
sudo docker exec -it deeplearning bash
nvidia-smi
cat /usr/local/cuda/version.txt
```

# connect internet
```

```

# rm all 
```
sudo docker stop $(docker ps) & docker rm $(docker ps -aq)
```
# save docker images
```
sudo docker commit containerId arron/deeplearning
sudo docker save -o 10.1-cudnn7-runtime-ubuntu18.04-pytorch1.3-tensorflow2.0.tar arron/deeplearning
```

# vim
```shell script
apt-get update
apt-get install vim
```

# 清华源
```shell script
cp /etc/apt/sources.list /etc/apt/sources.list.backup
rm /etc/apt/sources.list
vim /etc/apt/sources.list
```
```
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

```shell script
apt-get update
```

# oh-my-zsh
```bash
apt-get install zsh
apt-get install curl
apt-get install git
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```
```bash
vim ~/.zshrc
# update such as:
# plugins=(git zsh-autosuggestions)
source ~/.zshrc
```


# Miniconda
```bash
vim ~/.zshrc
```
```
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

```bash
source ~/.zshrc
```
```

# python

清华源
```
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```
豆瓣源
```
pip config set global.index-url https://pypi.doubanio.com/simple
```

# 
```
apt-get install gcc libglib2.0-dev libsm-dev libxrender-dev
```

# pytorch 1.3
文件太大，单独安装
https://pypi.tuna.tsinghua.edu.cn/packages/b4/0b/9d33aef363b6728ad937643d98be713c6c25d50ce338678ad57cee6e6fd5/torch-1.3.0-cp37-cp37m-manylinux1_x86_64.whl
https://pypi.tuna.tsinghua.edu.cn/packages/72/b9/5e22c25a201b80cd599af910200b66872af5f5404a13dc76e9ce1a988bed/torchvision-0.4.1-cp37-cp37m-manylinux1_x86_64.whl


```shell script


```

# tensorflow
同上

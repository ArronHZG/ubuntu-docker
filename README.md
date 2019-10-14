# build docker image
```
sudo docker pull nvidia/cuda:10.0-cudnn7-devel-ubuntu18.04
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
sudo docker run -d -it  -v /home/arron/dataset/:/root/dataset/ --gpus 2 --name deeplearning nvidia/cuda:10.0-cudnn7-devel-ubuntu18.04
```

# enter contatiners
```
sudo docker exec -it deeplearning /bin/bash
nvidia-smi
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
docker commit containerId arron/ubuntu16.04_tensorflow_remote
docker tag arron/ubuntu16.04_tensorflow_remote arron/ubuntu16.04_tensorflow_remote
# docker save -o [name].tar [name]:[tag]
docker save -o ubuntu16.04_tensorflow_remote-190917.tar arron/ubuntu16.04_tensorflow_remote
```

# python

```shell
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

```
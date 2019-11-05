# apt-get
```
sudo apt-get install exfat-utils make gcc

sudo add-apt-repository ppa:fossfreedom/indicator-sysmonitor
sudo apt-get install indicator-sysmonitor

sudo add-apt-repository ppa:apt-fast/stable
sudo apt-get install apt-fast

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
```

# ohmyzsh
	plugins
		zsh-autosuggestions
		sublime
		web-search
	theme
		agnoster
```
sudo apt-fast install zsh
sudo chsh -s /bin/zsh
reboot
sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

## Ubuntu 终端zsh的agnoster主题乱码
https://blog.csdn.net/CoderMannul/article/details/90724645

```
wget https://raw.githubusercontent.com/powerline/powerline/develop/font/10-powerline-symbols.conf
wget https://raw.githubusercontent.com/powerline/powerline/develop/font/PowerlineSymbols.otf
sudo mkdir /usr/share/fonts/OTF
sudo cp 10-powerline-symbols.conf /usr/share/fonts/OTF/
sudo mv 10-powerline-symbols.conf /etc/fonts/conf.d/
sudo mv PowerlineSymbols.otf /usr/share/fonts/OTF/
```


# ss
```
sudo apt-add-repository ppa:hzwhuang/ss-qt5
sudo apt-fast update
sudo apt-fast install shadowsocks-qt5s
```

# screen shot
ubuntu18.04
```
sudo apt-fast install flameshot
```
ubuntu16.04
```
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

# download
```
sudo add-apt-repository ppa:plushuang-tw/uget-stable
sudo apt-get update
sudo apt-fast install uget
sudo apt-fast install aria2

编辑”->“设置（S）……”，在弹出的界面中选择“插件”  选择插件匹配顺序“aria2”
```

# 安装包安装
- pycharm
- vscode
- sogou
- teamviewer
- miniconda

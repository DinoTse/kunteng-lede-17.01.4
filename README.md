
kunteng-lede-17.01.4是在LEDE 17.01.4的发行版本的基础上，增加了坤腾的开源插件以及我们精选的开源插件，

同时精简了编译步骤，针对国内的环境，优化了下载源，加快编译速度，降低了LEDE的开发编译门槛，

使开发者能用最快的速度编译出自己想要的固件。

## 编译步骤

下面我们以Ubuntu 16.04.2 LTS编译环境为例，一步一步编译出R7800固件

### 准备工作

首先，我们需要在ubuntu上安装如下软件包：

gcc， g++, binutils, bzip2, flex, python, perl, make,
find, grep, diff, unzip, gawk, getopt, subversion, libz-dev and libc 头文件

```
sudo apt-get update
sudo apt-get install gcc g++ build-essential subversion git-core libncurses5-dev zlib1g-dev gawk flex quilt libssl-dev xsltproc libxml-parser-perl mercurial bzr ecj cvs unzip
```
### 添加管理界面

```
./scripts/feeds update -a
./scripts/feeds install -a

```
### 选择编译目标

```
make menuconfig

    Target System (Qualcomm Atheros IPQ806X)  --->                                                      
    Target Profile (Netgear Nighthawk X4S R7800)  --->   
```

退出保存

### 编译固件

make V=s -j4

#### 如果编译遇到问题，使用 make V=s 看具体问题是什么

编译完成后

```
ubuntu:~/kunteng-lede$ ls bin/targets/ipq806x/generic/
config.seed                              lede-ipq806x-R7800-squashfs-sysupgrade.tar  lede-ipq806x-vmlinux.elf
lede-ipq806x-device-r7800.manifest       lede-ipq806x-squashfs-root.img              packages
lede-ipq806x-R7800-squashfs-factory.img  lede-ipq806x-ubifs-root.img                 sha256sums

```
其中lede-ipq806x-R7800-squashfs-factory.img即为R7800的工厂固件， lede-ipq806x-R7800-squashfs-sysupgrade.tar为升级固件

## 联系我们

加qq群 [331230369](https://jq.qq.com/?_wv=1027&k=4ADDSev)



### 如果您觉得我们的开源对您有帮助，请不要犹豫 star

[反馈&建议](https://github.com/KunTengRom/kunteng-lede-17.01.4/issues/new)


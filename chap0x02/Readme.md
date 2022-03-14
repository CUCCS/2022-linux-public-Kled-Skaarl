## H2

### 实验环境

- 本地环境（Ubuntu）

- 云环境（CentOS）

- ##### 配置asciinema

  ```
  sudo apt-add-repository ppa:zanchey/asciinema
  sudo apt-get update
  sudo apt-get install asciinema
  asciinema rec
  ```

###  实验过程

#### 1.在目标发行版上安装tmux和tshark；查看这2个软件被安装到哪些路径；卸载tshark;验证tshark卸载结果

- Ubuntu20.04

```
#安装tmux
sudo apt install tmux

#查看tmux当前安装路径
sudo apt-cache show tmux 或 dpkg -l softwarename

#安装tshark
sudo apt-get install tshark

#查看tshark安装路径
sudo apt-cache show tshark

#卸载tshark
sudo apt-get remove --purge tshark
```

[![asciicast](https://asciinema.org/a/smxOQbLq7p3evWqe0sICsPgeN.svg)](https://asciinema.org/a/smxOQbLq7p3evWqe0sICsPgeN)

- CentOS

```
#安装tmux
yum install tmux 

#查看tmux路径
rpm -qal |grep tmux

#安装tshark
yum install wireshark

#查看tshark安装路径
rpm -qal |grep wireshark

#卸载tshark
yum -y remove wireshark
```

[![asciicast](https://asciinema.org/a/WblGe8rewbEr4IbpAEOYRKUag.svg)](https://asciinema.org/a/WblGe8rewbEr4IbpAEOYRKUag)



#### 2.找到 `/tmp` 目录及其所有子目录下，文件名包含 `666` 的所有文件和找到 `/tmp` 目录及其所有子目录下，文件内容包含 `666` 的所有文件

- Ubuntu20.04

```
#文件名包含 `666` 的所有文件
sudo find . -name '*666*'

#文件内容包含 `666` 的所有文件
sudo grep -r "666" ./
```



[![asciicast](https://asciinema.org/a/Nn0FVrcMpS5B1BTmKnWX7f8WX.svg)](https://asciinema.org/a/Nn0FVrcMpS5B1BTmKnWX7f8WX)

- CentOS同上

#### 3.压缩与解压缩命令的使用方法

```
#压缩
zip -r haved.zip ~/test.txt
#解压缩
unzip -O cp936 -l homework.zip
```

[![asciicast](https://asciinema.org/a/cDafMtXahSiMWdTJBJd8gOb9a.svg)](https://asciinema.org/a/cDafMtXahSiMWdTJBJd8gOb9a)

#### 4.子进程管理

```
# 查看进程
ps aux | grep ping
```

[![asciicast](https://asciinema.org/a/8kBuNtTCNUDqbqefy0FdjzahX.svg)](https://asciinema.org/a/8kBuNtTCNUDqbqefy0FdjzahX)

#### 5.获取硬件信息（目标系统的CPU、内存大小、硬盘数量与硬盘容量）

- Ubuntu20.04

  ```
  # 查看物理CPU个数
  cat /proc/cpuinfo| grep "physical id"| sort| uniq| wc -l
  
  # 查看每个物理CPU中core的个数(即核数)
  cat /proc/cpuinfo| grep "cpu cores"| uniq
  
  # 查看逻辑CPU的个数
  cat /proc/cpuinfo| grep "processor"| wc -l
  
  # 查看总内存，剩余内存，可使用内存等信息  
  cat /proc/meminfo
  
  # 查看硬盘信息
  sudo fdisk -l
  ```

  [![asciicast](https://asciinema.org/a/bST678GMwuLgiG3ttGyWx1G0I.svg)](https://asciinema.org/a/bST678GMwuLgiG3ttGyWx1G0I)

- CentOS

  ```
  # 查看物理CPU个数
  cat /proc/cpuinfo| grep "physical id"| sort| uniq| wc -l
  
  # 查看每个物理CPU中core的个数(即核数)
  cat /proc/cpuinfo| grep "cpu cores"| uniq
  
  # 查看逻辑CPU的个数
  cat /proc/cpuinfo| grep "processor"| wc -l
  
  # 查看内存信息  
  free
  
  # 查看硬盘信息
  sudo fdisk -l
  ```

  [![asciicast](https://asciinema.org/a/3oe2Ry2n4tncF8A7qaf89bDw1.svg)](https://asciinema.org/a/3oe2Ry2n4tncF8A7qaf89bDw1)

### 问题与解决

- 文件解压缩时将文件目录弄混，导致文件压缩出错；
- 过滤文件内容grep命令通过查找文档的方式理解了具体使用方法；

### 结果汇总

|                                         |                         Ubuntu20.04                          |                            CentOS                            |
| :-------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|              **安装tmux**               |                    sudo apt install tmux                     |                       yum install tmux                       |
|        **查看tmux当前安装路径**         |       sudo apt-cache show tmux 或 dpkg -l softwarename       |                    rpm -qal \| grep tmux                     |
|             **安装tshark**              |                 sudo apt-get install tshark                  |                    yum install wireshark                     |
|         **查看tshark安装路径**          |                  sudo apt-cache show tshark                  |                  rpm -qal \| grep wireshark                  |
|             **卸载tshark**              |              sudo apt-get remove --purge tshark              |                   yum -y remove wireshark                    |
|     **文件名包含 `666` 的所有文件**     |                  sudo find . -name '*666*'                   |                              -                               |
|    **文件内容包含 `666` 的所有文件**    |                    sudo grep -r "666" ./                     |                              -                               |
|                **压缩**                 |                 zip -r haved.zip ~/test.txt                  |                              -                               |
|               **解压缩**                |                unzip -O cp936 -l homework.zip                |                              -                               |
|           **查看物理CPU个数**           | cat /proc/cpuinfo  \|   grep "physical id"  \| sort  \| uniq \| wc -l | cat /proc/cpuinfo  \| grep "physical id" \| sort \| uniq \| wd -l |
| **查看每个物理CPU中core的个数(即核数)** |       cat / proc/cpuinfo \| grep "cpu  cores" \| uniq        |                              -                               |
|          **查看逻辑CPU的个数**          |        cat /proc/cpuinfo \| grep "processor" \| wc -l        |                              -                               |
|            **查看内存信息**             |                      cat /proc/meminfo                       |                             free                             |
|            **查看硬盘信息**             |                        sudo fdisk -l                         |                              -                               |



### 参考资料

- [ubuntu 命令行卸载并清理软件（卸载的很干净）](https://blog.csdn.net/jiayoudangdang/article/details/79943065)
- [CentOS常用的文件操作命令总结](https://www.haorooms.com/post/centeros_wj_zj)
- [asciinema Docs]([How it works - asciinema](https://asciinema.org/docs/how-it-works))
- [Linux查看物理CPU个数、核数、逻辑CPU个数]([Linux查看物理CPU个数、核数、逻辑CPU个数 - emanlee - 博客园 (cnblogs.com)](https://www.cnblogs.com/emanlee/p/3587571.html))




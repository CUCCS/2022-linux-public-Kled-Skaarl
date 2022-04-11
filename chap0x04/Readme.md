## H4

### 实验环境：

- **Ubuntu 20.04.02 Server 64bit**
- **Vscode**

### 实验任务：

##### 1.用bash编写一个图片批处理脚本，实现以下功能：

- [x] 支持命令行参数方式使用不同功能

- [x] 支持对指定目录下所有支持格式的图片文件进行批处理指定目录进行批处理

- [x] 支持以下常见图片批处理功能的单独使用或组合使用

  - 支持对jpeg格式图片进行图片质量压缩

  - 支持对jpeg/png/svg格式图片在保持原始宽高比的前提下压缩分辨率

  - 支持对图片批量添加自定义文本水印

  - 支持批量重命名（统一添加文件名前缀或后缀，不影响原始文件扩展名）

  - 支持将png/svg图片统一转换为jpg格式

##### 2.用bash编写一个文本批处理脚本，对以下附件分别进行批量处理完成相应的数据统计任务：

- [x] 统计不同年龄区间范围（20岁以下、[20-30]、30岁以上）的球员数量、百分比
- [x] 统计不同场上位置的球员数量、百分比
- [x] 名字最长的球员是谁？名字最短的球员是谁？
- [x] 年龄最大的球员是谁？年龄最小的球员是谁？

##### 3.用bash编写一个文本批处理脚本，对以下附件分别进行批量处理完成相应的数据统计任务：

- [x] 统计访问来源主机TOP 100和分别对应出现的总次数
- [x] 统计访问来源主机TOP 100 IP和分别对应出现的总次数
- [x] 统计最频繁被访问的URL TOP 100
- [x] 统计不同响应状态码的出现次数和对应百分比
- [x] 分别统计不同4XX状态码对应的TOP 10 URL和对应出现的总次数
- [x] 给定URL输出TOP 100访问来源主机

### 实验要求：

- 继承第一章

- 所有源代码文件必须单独提交并提供详细的`-help`脚本内置帮助信息
- 任务二的所有统计数据结果要求写入独立实验报告

### 实验过程：

- #### 任务1

1.安装`imagemagick`

```bash
sudo apt-get update
sudo apt-get install imagemagick
```

2.编写[task1.sh](./code/task1.sh)

3.执行

![bash_task1.png](./img/bash_task1.png)

![bash](./img/bash_task2.png)

- #### 任务2

1.下载数据`wget https://c4pr1c3.github.io/LinuxSysAdmin/exp/chap0x04/worldcupplayerinfo.tsv`

2.编写[task2.sh](./code/tash2.sh)

3.执行结果见[task2-3_result.md](./task2-3_result.md)

- #### 任务3

1.下载数据`wget "https://c4pr1c3.github.io/LinuxSysAdmin/exp/chap0x04/web_log.tsv.7z"`后进行解压

```bash
 sudo apt-get install p7zip-full
 7z x web_log.tsv.7z 
```

2.编写[task3.sh](./code/task3.sh)

3.执行结果

![bash_task3.png](./img/bash_task3.png)

详情见[task2-3_result.md](./task2-3_result.md)

### 问题及解决：

在travis构建时发生报错：`convert:unable to read font (null)`，通过查看[资料](https://legacy.imagemagick.org/discourse-server/viewtopic.php?t=34911)发现可通过`apt-get install ghostscript`解决。

### 参考资料：

- [Linux awk](https://www.runoob.com/linux/linux-comm-awk.html)
- [Travis CI 极简教程](https://github.com/dunwu/dunwu.github.io/blob/master/tools/travis-ci%E6%9E%81%E7%AE%80%E6%95%99%E7%A8%8B.md)

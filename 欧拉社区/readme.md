# 列出需求及思考

项目名称：

**UEFI 启动的树莓派镜像**

仔细分析的文字：

**描述 树莓派（英语：Raspberry Pi）是基于 Linux 的单片机电脑，目的是以低价硬件及自由软件促进学校的基本计算机科学教育。为了降低成本，树莓派省去了传统计算机用来存储引导加载程序的板载存储器(BIOS), 直接把引导程序放在了SD卡中。目前树莓派 Pi 4 引入了 UEFI，不过目前处于 EXPERIMENTAL 状态。本项目目标是为树莓派引入 UEFI Firmware 来支持 UEFI 启动 openEuler 树莓派 4B。**

关键词：**UEFI Firmware** ，**树莓派 4B**

## UEFI 启动的树莓派镜像 

 难度很大，需补充很多相关知识，如
 
 **在树莓派的内核中加入引导**
 
 **树莓派内核是如何与openeuler结合的**
 
 **现在的引导机制**
 > 直接是BIOS？

## 镜像制作脚本和文档
### 构建自己的镜像
该部分待项目通过后，仔细了解，相应链接可以参考官方文档

[openEuler镜像的构建](https://gitee.com/openeuler/raspberrypi/blob/master/documents/openEuler%E9%95%9C%E5%83%8F%E7%9A%84%E6%9E%84%E5%BB%BA.md)

[交叉编译内核](https://gitee.com/openeuler/raspberrypi/blob/master/documents/%E4%BA%A4%E5%8F%89%E7%BC%96%E8%AF%91%E5%86%85%E6%A0%B8.md)

**预计会使用交叉编译的方式，完成项目镜像的交付**
因为对应的bash脚本，通俗意义上来理解，就是相应命令行的输入及相应环境的判断。该部分在完成UEFI 启动后较容易实现。

## 引入 UEFI 启动的相关文档

使用md格式，完成相应启动文档的编写。编写文档数量，由开发难度决定！！！
大体上可分为三个部分
> UEFI本身的相关解释 -> 记录完成中间过程（归档） -> 对外公布相应文档及教程

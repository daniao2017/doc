# openEuler镜像的构建

## 前言
今天按照[openEuler镜像的构建](https://gitee.com/openeuler/raspberrypi/blob/master/documents/openEuler%E9%95%9C%E5%83%8F%E7%9A%84%E6%9E%84%E5%BB%BA.md)文档跑了openEuler镜像的构建的过程。

```
开发环境    
鲲鹏通用计算增强型 | kc1.large.2 | 2vCPUs | 4GB
镜像 CentOS 7.4 64bit with ARM
```

## 注意事项

###  生成公钥上传到gitee
```
ssh-keygen #生成本机公钥
cat ~/.ssh/id_rsa.pub #查看本机公钥
```

### 安装依赖包

```
yum install openssl-devel
yum install bison
yum install flex
yum install dnf
```

尤其要注意`openssl-devel`,因为这包在CentOS与Ubuntu(`libssl-dev`)中叫法不一样！！！在这里面卡了好久！！！

### 服务器更换默认源

由于在下载包的初期，发现包的下载速度很不理想，就产生了更换镜像源的想法，这就是一个坑！！！

参考

[centos7配置国内yum源](https://blog.csdn.net/xiaojin21cen/article/details/84726193?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase)

[鲲鹏云（ARM64）如何配置华为提供的yum镜像源](https://blog.csdn.net/weixin_43928077/article/details/104946615?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase)

没有换源成功，一直提示404的错误，然后自己打开`https://mirrors.cnnic.cn/centos/7/os/`,发现系统里面根本没有提供ARM架构的，

换华为鲲鹏的镜像，发现他们对包与包之间的依赖处理不是很好。

最后还是系统默认源完成了下载，可能还是太菜了，，

需要补充一下yum的包管理知识！！！

## 进度

编译内核，制作引导都已经完成。

现在卡在制作根文件系统上了，尤其是

`dnf --installroot=${WORKDIR}/rootfs/ install dnf --nogpgcheck -y`
这个命令，提示
```
Warning: failed loading '/root/rootfs/etc/yum.repos.d/openEuler-20.03-LTS.repo', skipping.
There are no enabled repos.
```

待仔细了解`dnf`命令，及其他包管理知识

## 总结

该文档持续更新，得完成相应的镜像制作过程。当然对根文件系统我是不需要进行额外操作的。应该要补充一下树莓派firmware的知识，特别是上电启动到拉取内核的相应知识，应该着重关注Ubuntu/centos等镜像启动时候知识，进行类比！！！
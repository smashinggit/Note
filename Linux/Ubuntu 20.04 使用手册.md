



# 一、TODO



# 二、 VMware Tools



## 2.1 VMware Tools 的功能





## 2.2 安装 VMware Tools



1. 选择 VMware 菜单中的 虚拟机 -> **安装VMware Tools**。 或者点击下图中的 **安装Tools**

![](C:\Users\Administrator\Desktop\安装 VMware Tools_1.png)



2. 会在虚拟机界面中出现一个弹框，选择是

![](C:\Users\Administrator\Desktop\安装 VMware Tools_2.png)



3. 打开文件管理窗口，左边找到 **VMware Tools**， 打开后里面有个gz压缩包

![](C:\Users\Administrator\Desktop\安装 VMware Tools_3.png)



4. 把这个压缩包复制到我们自己的用户文档文件夹中（位置随意，图中是放到了新建的名称为 VMwareTools 的文件夹内）

![](C:\Users\Administrator\Desktop\安装 VMware Tools_4.png)

5.  双击使用解压工具进行解压，也可使用命令行 tar -xzvf VMwareTools-10.3.23-16594550.tar.gz 进行解压。

   解压后发现里面的文件中有个 vmware-install.pl 文件。

![](C:\Users\Administrator\Desktop\安装 VMware Tools_5.png)

6. 在这个解压后的文件夹中，鼠标移动到空白区域， 右键--**在终端打开**

![](C:\Users\Administrator\Desktop\安装 VMware Tools_6.png)



7. 在终端中输入 sudo ./vmware-install.pl 。 之后按照系统提示，输入 yes 或者 提示的目录。 

![](C:\Users\Administrator\Desktop\安装 VMware Tools_7.png)



当出现以下信息时，证明安装成功

![](C:\Users\Administrator\Desktop\安装 VMware Tools_8.png)



8. 重启系统即可。





# 三、调整虚拟内存













# 四、更换软件源

ubuntu更换镜像分为以下几个步骤：

1. 备份原来的源

2. 更换XX源

3. 更新



## 4.1 不同镜像原地址

将系统原文件中镜像地址全部更改为国内的镜像源地址，可以更改为以下任意一个地址（使用比较多的镜像源地址阿里，网易，清华，中科大镜像源地址），保存即可。



**阿里源**

```
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse    
```

**网易源**

```
 deb http://mirrors.163.com/ubuntu/ bionic main restricted universe multiverse
 deb http://mirrors.163.com/ubuntu/ bionic-security main restricted universe multiverse
 deb http://mirrors.163.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ bionic main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ bionic-backports main restricted universe multiverse
```

**清华源**

```
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
```

**中科大源**

```
deb https://mirrors.ustc.edu.cn/ubuntu/ bionic main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
```



## 4.2 更换源文件

1. 备份

   ```
   sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup 
   ```

   

2. 修改源文件数据，将sources.list里面的地址替换成上面的国内镜像地址

   ```
   sudo vi /etc/apt/sources.list
   ```

   

3. 更换好源之后执行下面命令更新

   ```
   sudo apt-get update
   ```

   

4. 更新软件

   ```
   sudo apt-get upgrade
   ```

   


















# Vim





## 命令模式

### 移动光标

vi可以**直接用键盘上的光标键来上下左右移动**，但正规的vi的用法是用小写英文字母h、j、k、l，分别控制光标左、下、上、右移一格。常用的光标操作还有以下几种情况。

 - **按「ctrl」+「b」：屏幕往"后"移动一页。**
 - 按「ctrl」+「f」：屏幕往"前"移动一页。
 - 按「ctrl」+「u」：屏幕往"后"移动半页。
 - 按「ctrl」+「d」：屏幕往"前"移动半页。
 - **按数字「0」：移到文章的开头。**
 - **按「G」：移动到文章的最后。**
 - 按「$」：移动到光标所在行的"行尾"。
 - 按「^」：移动到光标所在行的"行首"
 - 按「w」：光标跳到下个字的开头
 - 按「e」：光标跳到下个字的字尾
 - 按「b」：光标回到上个字的开头
 - 按「#l」：光标移到该行的第#个位置，如：5l,56l。



### 删除

 - **「x」：每按一次，删除光标所在位置的"后面"一个字符。**
 - **「#x」：例如，「6x」表示删除光标所在位置的"后面"6个字符。**
 - 「X」：大写的X，每按一次，删除光标所在位置的"前面"一个字符。
 - 「#X」：例如，「20X」表示删除光标所在位置的"前面"20个字符。
 - **「dd」：删除光标所在行。**
 - **「#dd」：从光标所在行开始删除#行**

### 复制

- 「yw」：将光标所在之处到字尾的字符复制到缓冲区中。
- 「#yw」：复制#个字到缓冲区
- 「yy」：复制光标所在行到缓冲区。
- 「#yy」：例如，「6yy」表示拷贝从光标所在的该行"往下数"6行文字。
- 「p」：将缓冲区内的字符贴到光标所在位置。注意：所有与"y"有关的复制命令都必须与"p"配合才能完成复制与粘贴功能。

### 跳至指定的行

- 「ctrl」+「g」列出光标所在行的行号。
- 「#G」：例如，「15G」，表示移动光标至文章的第15行行首。





## 插入模式







## 末行模式



在使用「last line mode」之前，请记住先按「ESC」键确定您已经处于「command mode」下后，再按「：」冒号即可进入「last line mode」



### **列出行号**

- 「set nu」：输入「set nu」后，会在文件中的每一行前面列出行号。

  

### **跳到文件中的某一行**

- 「#」：「#」号表示一个数字，在冒号后输入一个数字，再按回车键就会跳到该行了，如输入数字15，再回车，就会跳到文章的第15行。

  

### **查找字符**

- 「/关键字」：先按「/」键，再输入您想寻找的字符，如果第一次找的关键字不是您想要的，可以一直按「n」会往后寻找到您要的关键字为止。

- 「?关键字」：先按「?」键，再输入您想寻找的字符，如果第一次找的关键字不是您想要的，可以一直按「n」会往前寻找到您要的关键字为止。

  

### **保存文件**

- 「w」：在冒号输入字母「w」就可以将文件保存起来。



### 退出

- 「q」：按「q」就是退出，如果无法离开vi，可以在「q」后跟一个「!」强制离开vi。
- 「qw」：一般建议离开时，搭配「w」一起使用，这样在退出的时候还可以保存文件。



# 用户





## sudo

sudo命令用于切换用户身份执行，语法格式如下：

> sudo [选项] <命令> ...

它允许当前用户以root或其他普通用户的身份来执行命令，使用选项-u指定用户要切换的身份，默认为root身份



## su

使用su命令临时改变用户身份，可让一个普通用户切换为超级用户或其他用户，并可临时拥有所切换用户的权限

> su [选项] [用户登录名]

多数Linux版本中不带任何参数的su命令会将用户提升至root权限，前提是需要提供root密码。
**由于Ubuntu限制严格，默认不提供root密码，也就不能直接使用su命令升至root权限，而必须使用sudo来获得root权限**。
如果要临时变成root身份，可以执行sudo su root命令，前提是当前用户具备sudo命令权限（属于admin组即可）







# 软件包管理



Linux提供了多种软件安装方式，从最原始的源代码编译安装到最高级的在线自动安装和更新。**Ubuntu主要使用Deb软件包格式。**



## 软件包安装软件

软件包将应用程序的二进制文件、配置文档和帮助文档等合并打包在一个文件中，用户只需使用相应的软件包管理器来执行软件的安装、卸载、升级和查询等操作。软件包中的可执行文件是由软件发布者进行编译的，这种预编译的软件包重在考虑适用性，通常不会针对某种硬件平台优化，它所包含的功能和组件也是通用的。

目前主流的软件包格式有两种：RPM和Deb。



### RPM

RPM是RedHat Package Manager（软件包管理器）的缩写，是由Red Hat公司提出的一种软件包管理标准，文件后缀名为.rpm。这种文件格式名称虽然有RedHat的标志，但是其设计理念是开放式的，加之功能十分强大，已成为目前Linux各发行版本中应用最广泛的软件包格式之一。可以使用rpm工具来管理RPM软件包。



### Deb

Deb是Debian Packager的缩写，是Debian和Ubuntu系列发行版本上使用的软件包格式（文件后缀名为.deb），需要使用dpkg命令进行管理。dpkg是Debian Packager的简写，用于安装、更新、卸载Deb软件包，以及提供Deb软件包相关的信息。



当然，**使用RPM或Deb软件包安装也需要考虑依赖性问题，只有应用程序所依赖的库和支持文件都正确安装之后，才能完成软件的安装**。**现在的软件依赖性越来越强，单纯使用这种软件包安装效率很低**，难度也不小，为此推出了高级软件包管理工具。





## 高级软件包管理工具



**高级软件包管理工具能够通过Internet主动获取软件包，自动检查和修复软件包之间的依赖关系，实现软件的自动安装和更新升级，大大简化了Linux系统上安装、管理软件的过程**。这种工具需要通过Internet从后端的软件库下载软件，适合在线使用。目前主要的高级软件包管理工具有Yum和APT两种，另外有一些商业版的工具则由Linux发行商专门提供



### Yum

Yum（Yellow dog Updater，Modified）是一个基于RPM包的软件包管理器，能够从指定的服务器自动下载RPM包并且完成安装，可以处理依赖性关系，并且一次安装所有依赖的软件包，无需用户繁琐地一次次下载、安装。Red Hat Enterprise Linux、CentOS、Fedora等Linux发行版采用Yum。



### APT

APT（Advanced Packaging Tools）可译为高级软件包工具，是Debian及其派生发行版（如Ubuntu）的软件包管理器。APT可以自动下载、配置、安装二进制或者源代码格式的软件包，甚至只需一条命令就能更新整个系统的所有软件。APT最早被设计成dpkg工具的前端，用来处理Deb格式的软件包。现在经过APT-RPM组织修改，RPM版本的APT已经可以安装在使用RPM的Linux发行版上。





## Ubuntu软件安装方式

作为主流的Linux桌面版，Ubuntu支持多种软件方式。**Ubuntu主要使用Deb软件包，建议用户首选APT工具。**

### Ubuntu软件中心

对于Ubuntu官方仓库中的软件，可以通过利用Ubuntu软件中心自动从后端的软件源下载安装，能让用户安装和卸载许多流行的软件包。这实际上是软件源安装的一种方式，也是Ubuntu桌面版中最简单、最容易的安装方式。



### APT工具

APT是另一种软件源安装方式，效率比Ubuntu软件中心要高，可以自动获取、安装和更新升级软件包，是首选的Ubuntu软件安装方式。Ubuntu分别针对命令行界面和图形界面提供了APT工具，命令行工具是apt，图形界面工具是新立得软件包管理器（Synaptic）。



### PPA安装

APT和Ubuntu软件中心都是软件源安装方式，通常从Ubuntu官方仓库中获取软件。考虑到稳定性，Ubuntu官方仓库收录的软件比较正式，版本相对滞后。对于一些没有收录到Ubuntu官方仓库的软件，可以通过PPA这种非正式的软件仓库提供。

PPA是Personal Package Archive的缩写，可以译为个人软件包档案。使用PPA，软件制作者可以轻松地发布软件，并且能够准确地对用户进行升级。Ubuntu用户可以使用PPA源在第一时间体验到最新版本的软件。APT和Ubuntu软件中心都可以添加PPA安装源。



### Dpkg工具

上述几种软件源安装都需要在线操作，而**获得Deb安装包后，可以直接使用dpkg命令工具进行离线安装，无需联网**。这是Ubuntu传统的软件安装方式，**最大的困难是要自行处理软件依赖性问题**。

对于RPM包，Ubuntu不能直接进行安装，需要使用alien工具将其转换为Deb包格式，再使用dpkg进行安装。不过最好不要使用这种方式，应尽可能直接获得Deb包。



### 其他二进制软件包

有些软件直接采用二进制包方式发布，常用的格式有bin和run，此类软件在命令行运行安装文件即可，或者在图形界面文件管理器中双击该软件包执行，前提是为该软件包文件赋予可执行权限



### 源代码安装

上述安装方式基本上都属于预编译安装，提供现成的二进制文件。但有时不得不采用最原始的源代码安装方式，下载软件源代码进行编译之后再自行安装。例如，有的开发商只提供软件源代码，有的二进制软件包的软件版本不符合自己的要求，或者要对软件多一些定制，一般就要考虑到获得源代码，根据软件说明文档编译安装。这种方式最为通用，适用于各种Linux发行版，但是安装过程最复杂，难度最大。



## 软件源

APT的软件源在Ubuntu安装时已经初始设置，提供Ubuntu官方的网络安装来源。用户也可以使用系统安装光盘作为安装源，或从非官方的软件源中下载非官方的软件。除了直接下载二进制格式的Deb包外，也支持下载源代码软件，自行编译、安装。

Ubuntu的/var/lib/apt/lists目录存放的是已经下载的各软件源的元数据（metadata），这些数据是系统更新和软件包查找工具的基础。Ubuntu软件中心、APT（包括新立得软件包管理器）和软件更新器（Update Manager）等工具就是利用这些信息来更新和安装软件的。Ubuntu软件中心和APT安装和卸载软件的信息来源是/var/lib/dpkg/states，查询软件的信息来源是/var/lib/apt/lists。

软件更新器将系统已经安装的软件版本信息（存放在/var/lib/dpkg/states目录）与/var/lib/apt/lists/目录中同名的软件版本进行比较，以判断是否更新，然后将所有需要更新的软件在窗口中列出。





## APT

作为高级软件包工具，APT主要具备以下3项功能：

- 从Internet上的软件源下载最新的软件包元数据、二进制包或源代码包。软件包元数据就是软件包的索引和摘要信息文件。
- 利用下载到本地的软件包元数据，完成软件包的搜索和系统的更新。
- 安装和卸载软件包时自动寻找最新版本，并自动解决软件的依赖关系。

**使用APT工具安装、卸载、更新升级软件，实际上是通过调用底层的dpkg来完成的。**

APT会从每一个软件源（软件仓库）下载一个软件包的列表到本地，列表中提供有软件源所包含的可用软件包的信息。**多数情况下，APT会安装最新的软件包，被安装的软件包所依赖的其他软件包也会安装，建议安装的软件包则会给出提示信息，但不会安装**。

也有APT因依赖关系不能安装软件包的情况。例如，某软件包和系统中的其他软件包冲突，或者该软件包依赖的软件包在任何软件源中均不存在或没有符合要求的版本。遇到这种情况，APT会返回错误信息并且终止，用户需要自行解决软件依赖问题。



常用的APT命令行工具有两个，

- apt-get  用于执行与软件包安装有关的所有操作

- apt-cache  用于查询软件包的相关信息。

  

### apt-cache

使用APT工具安装和卸载软件包时必须准确地提供软件包的名字。

**apt-cache命令用于在APT的软件包缓存中搜索软件，收集软件包信息，获知哪些是可以在Ubuntu或Debian上安装的软件**。由于支持模糊查询，apt-cache查询非常方便。



- apt-cache pkgnames

执行pkgnames子命令列出当前所有可用的软件包

- apt-cache search 软件包名

使用子命令search查找使用参数定义的软件包并列出该软件包的相关信息，
参数可以使用正则表达式，最简单的是直接使用软件部分名字，将列出包含该名字的所有软件

- apt-cache show 包名

使用子命令show可以查看指定名称的软件包的详细信息

- apt-cache depends 包名

使用子命令depends可以查看软件包所依赖的软件包

- apt-cache rdepends 包名

使用子命令rdepends可以查看软件包被哪些软件包所依赖。

- apt-cache showpkg 包名

使用子命令showpkg查看软件包的依赖关系信息

- apt-cache policy 包名

使用子命令showpkg查看软件包的依赖关系信息



### apt-get

命令apt-get会自动帮助用户下载并安装所需的程序包或代码。**apt-get命令一般需要root权限执行，所以还要使用sudo命令**。

> sudo apt-get [选项] 子命令



- apt-get update

获取最新软件包列表，同步 /etc/apt/sources.list 和 /etc/apt/sources.list.d 中列出的软件源的索引，确保用户能够获得最新的软件包

- apt-get upgrade

获取最新软件包列表，同步 /etc/apt/sources.list 和 /etc/apt/sources.list.d 中列出的软件源的索引，确保用户能够获得最新的软件包

- apt-get install

下载安装软件包，并自动解决依赖关系

- apt-get remove

卸载指定的软件包

- apt-get autoremove 

自动卸载所有未使用的软件包

- apt-get purge

卸载指定的软件包及其配置文件

- apt-get source

下载软件包的源代码

- apt-get clean 

清理已下载的安装包，实际上是清除 /var/cache/apt/archives 目录下的软件包，不会影响软件的正常使用

- apt-get autoclean

删除已经卸载的软件的软件包备份



**APT会将下载的Deb包缓存在硬盘上的目录/var/cache/apt/archives中**，已安装或已卸载的软件包的Deb文件都备份在该目录下。

为释放被占用的空间，可以执行命令apt-get clean来删除已安装的软件包的备份，这样并不会影响软件的使用。

如果要删除已经卸载的软件包的备份，可以执行命令apt-get autoclean。



### 配置APT源

Ubuntu使用文本文件/etc/apt/sources.list来保存软件包的安装和更新源的地址。

另外与该文件功能相同的是/etc/apt/sources.list.d/目录下的.list文件，为在单独文件中写入安装源的地址提供了一种方式，通常用来安装第三方软件。

执行apt-get update就是同步（更新）/etc/apt/sources.list和/etc/apt/sources.list.d目录下的.list文件的软件源的索引，以获取最新的软件包。



## dpkg

除了使用APT工具在线安装软件外，有时可能还需要直接安装下载的软件包文件。Ubuntu主要使用Deb软件包格式，有些软件以.run或.bin二进制格式的包发布。

**Deb软件包需要使用dpkg工具进行管理**。dpkg本身是一个底层的工具，而APT则是位于其上层的工具，用于从远程获取软件包以及处理复杂的软件包关系。



>  dpkg -l 软件包名

查看Deb软件包，使用选项-l列出软件包的简要信息，包括状态、名称、版本、架构和简要描述。
如果不加软件包名参数，将显示所有已经安装的Deb包，包括显示版本以及简要说明。



结合管道操作再使用grep命令可以查询某些软件包是否安装，例如：

```
dpkg -l | grep zip 
```

可以使用选项-s来查看软件包状态的详细信息，例如查看软件包zip的状态。

> dpkg -s zip





### 安装Deb软件包

首先要获取Deb软件包文件，然后使用选项-i安装Deb软件包

> sudo dpkg -i 软件包文件名

软件包文件是Deb格式的，扩展名通常为.deb。
安装软件需要root权限，所以这里需要sudo命令。

如果以前安装过相同的软件包，执行此命令时会先将原有的旧版本删除。所有的软件包安装之前必须保证所依赖的库和软件已经安装到系统上，一定要清楚依赖关系



### 卸载Deb软件包

卸载软件包可以使用选项-r，命令格式如下：　

> 　sudo dpkg -r 软件包名

选项-r删除软件包的同时会保留该软件的配置信息，如果要将配置信息一并删除，应使用选项-P，格式如下：　　

> sudo dpkg -P 软件包名

使用dpkg工具卸载软件包不会自动解决依赖性问题，所卸载的软件包可能含有其他软件所依赖的库和数据文件，这种依赖关系需要妥善解决。



## run与.bin二进制包软件包安装



run程序安装包实质上是由一个安装脚本加上要安装的程序合成的一个文件，文件名后缀为.run。
.run文件的安装很简单，首先要为该文件增加可执行属性，可以执行以下命令来实现。

> 　sudo chmod +x 文件名.run

然后在终端中执行该文件即可，格式如下：

> 　sudo ./文件名.run

或者在图形界面中双击该文件执行。



要卸载使用run安装包安装的软件，需要到安装目录中查看帮助文档，通常该目录中会提供反安装脚本uninstall，可以切换到该安装目录执行此脚本。

> 　　sudo ./uninstall



bin安装包与run安装包类似，也是Linux系统上的一种自执行文件。在执行.bin文件之前，也需要赋予执行权限，安装与卸载过程可以参照run安装包。





## 更换软件源



buntu更换镜像分为以下几个步骤：Step1:备份原来的源；Step2:更换XX源；Step3:更新

### 不同镜像原地址

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



### 更换源文件

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

   






















































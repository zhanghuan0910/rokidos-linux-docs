# 搭建编译环境

这里介绍如何设置本地工作环境来编译 RokidOS 开源项目。目前只支持 Linux OS。

## 选择代码分支配置

如果您需要使用最新的开发中的 RokidOS 代码，您可以选择 rokidbase.xml 来编译目前最新的代码，我们的对外代码服务器，在每天凌晨4点会同步到对外访问服务器上。

如果您需要使用经过发布测试的 RokidOS 代码，请您选择我们对外发布列表中，指定有效的 REL 版本的 manifest 配置文件。 

## 设置 Linux 编译环境

### *64-bit* Ubuntu 系统

1. 安装 Ubuntu (>= 14.04) 64位系统。
2. 安装编译必须的软件包：
	```
        sudo apt-get install git-core gnupg cscope ctags libz-dev libexpat-dev \
          python language-pack-en texinfo \
          build-essential g++ git bison flex unzip \
          libssl-dev libxml-simple-perl libxml-sax-perl libxml2-dev libxml2-utils xsltproc \
          wget bc ccache curl
	```

### 配置USB使用权限

为了方便开发者开发过程中对设备软件进行更新或系统配置，我们在 RokidOS 系统上移植了Android的adbd服务，为保障您能正常使用 adb 连接到设备，请您按照[USB 设备识别配置](http://snowdream.github.io/51-android/)中介绍的方法来配置您的系统，让 Ubuntu 能正确识别RokidOS 的开发板。

## 下载源码
编译环境配置完成，接下来就可以[下载源代码](downloading_codes.md)了。

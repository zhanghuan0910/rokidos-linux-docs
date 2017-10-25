# 下载源代码

我们使用Google公司的Gerrit系统来管理我们的 RokidOS 源代码。

对外开放的 RokidOS 源代码，每天凌晨4点自动同步。

## 安装repo 工具

1. 确保主目录下有一个 bin/ 目录，并且该目录包含在路径中：
```
$ mkdir ~/bin
$ PATH=~/bin:$PATH
```
2. 根据您的办公网络情况，获取 repo 工具。
	* 可以翻墙 

		如果您的办公环境可以翻墙访问 Google 网站，您可以使用Google 官方发行的 repo 工具。
		```
		$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
		$ chmod a+x ~/bin/repo
		```

	* 不能翻墙

		如果您的办公环境可以不能访问 Google 网站，您可以使用Rokid 修正版的 repo 工具。
		```
		$ curl http://scm-deps-library.rokid-inc.com/linux/buildroot_dl_aml/repo > ~/bin/repo
		$ chmod a+x ~/bin/repo
		```
	
## 初始化 repo 客户端



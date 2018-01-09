# 网络接入配置

网络配置是必须做的，因为我们的设备是基于云端语音服务的交互设备，网络接入是保证系统正常工作的基础。
这里介绍如何配置网络，主要分为蓝牙配网和手动配网。

## 蓝牙配网
下载 [Rokid 官方手机App](http://s.rokidcdn.com/app/m_index.html)，安装后，打开 App，点击左上角，找到“若琪设置”==>“添加新设备”，如下图：
下载 Rokid APP，安装后，打开 APP 并登录后，若当前账号无绑定的设备则直接跳转到添加新设备页面，如下图：

![network_connect](../../files/network_connect.png) 

在图中椭圆红圈处, 点击5次，进入开发板蓝牙配网界面，即可开始配网，配网成功后将有语音提示配网成功。

## 手动配网
通过执行以下五个命令进行配网，然后 ifconfig 查看是否获得 ip 地址。
1. adb shell 登录 RokidOS
2. vi /data/system/wpa_supplicant.conf
```
	ctrl_interface=/var/run/wpa_supplicant
	ap_scan=1
	update_config=1
	network={
        	ssid="wifi名"
		psk="wifi密码"
	}
```
3. sync
4. wpa_cli reconfigure
5. systemctl restart dhcpcd

# WiFi服务

wifi网络提供了一个网络检测服务，来判断当前的wifi连接状态，同时这也是运用上述API实现的一个demo，当检测到网络断开时，会通过dbus的通信协议像ams上报网络断开消息。

wifi_monitor代码路径: robot/services/wifi_monitor

流程图如下：

![wifi_monitor](../../files/wifi_monitor.png)

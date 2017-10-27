# WiFi控制

ROKIDOS将一些常用wifi控制函数已经封装成接口，并提供通用API方便开发者进行扩展。

## Station模式API

现有基本上所有的linux内核嵌入式wifi设备都支持wpa_supplicant进行wifi station模式的管理和配置。所以ROKIDOS也是将wifi控制封装成wpa_supplicant控制接口。第三方开发者也可以移植到其他依赖于wpa_supplicant控制的第三方设备中。代码相关路径位于robot/external/wpa_ctrl，常用接口如下：


```c
// connect network ssid : net->ssid psk: net->psk key :net->key_mgmt
int wifi_join_network(struct wifi_network *net);

// join network need reset dhcp
void dhcp_reset();

// save current ssid psk config to wpa_supplicant.conf
int wifi_save_network();

// get current ap signal
int wifi_get_signal(int *sig);

// get current wifi status
int wifi_get_status(int *status);

// get wifi ap list , must after scan 
int wifi_get_scan_result(struct wifi_scan_list *list);

// get current net status by ping taobao
int network_get_status(int *status);

// get list network , return num:1 have configed
int wifi_get_listnetwork(int *num);

// trigger wifi scan 
int wifi_scan();

// get wpa_supplicant monitor socket
int wifi_connect_moni_socket(const char * path);

// get monitor socket data
int wifi_ctrl_recv(char *reply, int *reply_len);

// close monitor socket
void wifi_monitor_release();
```

我们同时提供了一个通用接口，我们上述所有接口均是通过这个接口来实现的。后续我们也会丰富更多的wifi接口。

```c
// current supplicant cmd
enum {
    WIFI_COMMAND_SCAN,
    WIFI_COMMAND_ADDNETWORK,
    WIFI_COMMAND_SETNETWORK_SSID,
    WIFI_COMMAND_SETNETWORK_PSK,
    WIFI_COMMAND_SETNETWORK_KEYMETH,
    WIFI_COMMAND_ENABLENETWORK,
    WIFI_COMMAND_SELECTNETWORK,
    WIFI_COMMAND_RECONFIGURE,
    WIFI_COMMAND_REATTACH,
    WIFI_COMMAND_GET_STATUS,
    WIFI_COMMAND_GET_SIGNAL,
    WIFI_COMMAND_SAVECONFIG,
    WIFI_COMMAND_SCAN_R,
    WIFI_COMMAND_LISTNETWORK,
}WIFI_COMMAND;

int wifi_send_command(int cmd, void *value, int val_len, void *res, int res_len);
```
## AP模式API

还在开发中。。。

## 配网
ROKIDOS配套的开发板支持wifi连接internet，系统提供了一些控制wifi连接的接口，配网业务及网络监控服务。设备第一次连接网络需要第三方设备发送wifi相关信息如SSID，PSK和加密方式到设备，第一次联网方式支持如下方式：

### 蓝牙配网

### AP模式配网

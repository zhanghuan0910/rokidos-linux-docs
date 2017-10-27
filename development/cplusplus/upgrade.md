# 系统升级

根据[系统升级](../../porting/upgrade/upgrade.md)介绍，应用层接口只需写入misc分区标志位接口。

## 接口
上层应用程序由nodejs调用，底层提供了librecovery C库，此库提供了写升级标志的接口，第三方厂商可以根据此进行修改自己的ota升级。

```c
struct boot_cmd {
    char boot_mode[32];               // 升级模式
    char recovery_path[256];          // 固件路径
    char recovery_state[32];          // 升级状态
};

int get_recovery_cmd_status(struct boot_cmd *cmd);
int set_recovery_cmd_status(struct boot_cmd *cmd);
```

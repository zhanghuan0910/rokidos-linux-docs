# btflinger

btflinger是RokidOS提供的蓝牙服务

# 以下为相关的接口：

    int bluetooth\_rokid\_open\(char \*name\);

int bluetooth\_rokid\_close\(void\);

int bluetooth\_rokid\_use\_a2dp\(void\);

int bluetooth\_rokid\_a2dp\_query\(void\);

int bluetooth\_rokid\_use\_a2dp\_link\(char choice\);

int bluetooth\_rokid\_use\_a2dp\_sink\(void\);

int bluetooth\_rokid\_use\_ble\(char \*name\);

int bluetooth\_rokid\_use\_ble\_close\(void\);

int bluetooth\_rokid\_use\_avrcp\_cmd\(enum bluetooth\_avrcp\_cmd cmd\);

int bluetooth\_rokid\_send\_a2dp\_rsp\(bd\_g bd\_gr\);

int bluetooth\_rokid\_send\_ble\_rsp\(unsigned char \*value, unsigned short length\);

int bluetooth\_rokid\_get\_ble\_rsp\(struct bt\_ble\_rsp\_msg  \*message\);

int bluetooth\_rokid\_get\_a2dp\_rsp\(struct bt\_a2dp\_rsp\_msg \* message\);




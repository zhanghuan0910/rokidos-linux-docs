# btflinger

btflinger是RokidOS提供的蓝牙服务

# 以下为相关的接口：

`int bluetooth_rokid_open(char *name);`

`int bluetooth_rokid_close(void);`

`int bluetooth_rokid_use_a2dp(void);`

`int bluetooth_rokid_a2dp_query(void);`

`int bluetooth_rokid_use_a2dp_link(char choice);`

`int bluetooth_rokid_use_a2dp_sink(void);`

`int bluetooth_rokid_use_ble(char *name);`

`int bluetooth_rokid_use_ble_close(void);`

`int bluetooth_rokid_use_avrcp_cmd(enum bluetooth_avrcp_cmd cmd);`

`int bluetooth_rokid_send_a2dp_rsp(bd_g bd_gr);`

`int bluetooth_rokid_send_ble_rsp(unsigned char *value, unsigned short length);`

`int bluetooth_rokid_get_ble_rsp(struct bt_ble_rsp_msg  *message);`

`int bluetooth_rokid_get_a2dp_rsp(struct bt_a2dp_rsp_msg * message);`




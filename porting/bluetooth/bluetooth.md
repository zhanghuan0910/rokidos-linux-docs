# 蓝牙相关代码目录：

buildroot/package/aml\_brcm\_bsa:博通模组厂商提供的代码包，主要是mk file和config.in文件

vendor/broadcom/brcm-bsa：以上代码包实际所包含的的代码所在

rokid\_br\_external/package/btflinger：蓝牙的service的代码包，主要是mk file和config.in文件，相关启动脚本

robot/services/btflinger：以上代码包实际所包含的的代码所在

├── api                                             接口文件

│   ├── bluetooth\_msgque.c

│   ├── btflinger\_api.c

├── include                                     接口相关头文件

│   ├── bluetooth\_msgque.h

│   └── btflinger\_api.h

├── src                                            service源代码，启动脚本。 源代码暂时不开放，只提供bin文件

│   ├── bsa\_server\_service\_ctl.sh

│   ├── btflinger

│   ├── bt\_service\_ctl.sh

├── test                                           模块测试文件，接口的调用方法可以参考此文件

│   ├── bluetooth\_test.c

# 更新代码后如果发生编译通不过或者运行时错误的情况：

```
  删掉 output/banban\_m\_a113/build/aml\_brcm\_bsa-0107\_00.26.00/

  删掉 output/banban\_m\_a113/build/btflinger

  再重新make
```

# 如果模组相同，只是迁移平台：

```
 将相关代码目录直接覆盖过去即可：

  buildroot/package/aml\_brcm\_bsa

  vendor/broadcom/brcm-bsa

  rokid\_br\_external/package/btflinger

  robot/services/btflinger
```

# 如果模组切换，则还需要增加的步骤：

```
 修改robot/services/btflinger/src/bsa\_server\_service\_ctl.sh


将红框处的路径修改成新的模组的固件的路径即可

注意：目前只支持在博通的模组间切换，如果是非博通的模组目前暂时不支持。
```

# 如果厂商需要定义自己的BLE的UUID：

```
 修改rokid\_br\_external/configs/rokid\_common\_packages.frag文件
```




# 刷机说明


### Amlogic芯片

* 生成的镜像位置

```
output/<开发板型号>/images
	├── aml_upgrade_package.conf     # << 分区配置信息
	├── aml_upgrade_package.img	 # << Amlogic 官方工具刷机包
	├── boot.img			 # << 可 fastboot 刷机镜像，kernel、ramdisk 分区
	├── dtb.img -> ./banban_m_a113.dtb # << 可 fastboot 刷机镜像，这是一个软链接，实际刷机时用指向的镜像
	├── Image.gz
	├── keys.conf
	├── banban_m_a113.dtb
	├── platform.conf
	├── recovery.img		# << 可 fastboot 刷机镜像，OTA 功能主体
	├── rokid_upgrade_package.conf  # << 仅用于 OTA 升级，指示分区信息，刷机不需要
	├── rokid_upgrade_package.img   # << 后台 OTA 升级的镜像，刷机不需要
	├── rootfs.cpio
	├── rootfs.cpio.gz
	├── rootfs.cpio.uboot
	├── rootfs.ext2			# << 可 fastboot 刷机镜像，系统分区用这个镜像，该镜像没有做过压缩
	├── rootfs.ext2.img2simg
	├── rootfs.ext4 -> rootfs.ext2
	├── rootfs.tar
	├── rootfs.tar.gz
	├── u-boot.bin			# << 可 fastboot 刷机镜像，bootloader 分区
	├── u-boot.bin.encrypt
	├── u-boot.bin.encrypt.efuse
	├── u-boot.bin.encrypt.sd.bin
	├── u-boot.bin.encrypt.usb.bl2
	├── u-boot.bin.encrypt.usb.tpl
	├── u-boot.bin.sd.bin
	├── u-boot.bin.usb.bl2
	└── u-boot.bin.usb.tpl
```

* 官方刷机方式
	

	1. 安装 Amlogic 官方刷机工具( Windows 版本)
		具体安装步骤，请参阅[Amlogic官方刷机工具](../../files/AmlUSBBurning.pdf)。

	2. 选择刷机镜像


	3. 进入刷机模式


	4. 开始刷机 

* fastboot 刷机方式
	1. 进入 fastboot 模式
		* 开发板是 Linux 系统
	
		[TBD]	

		* 开发板是 Android 系统

		[TBD]	

	2. 刷机指令

	[TBD]	

	3. 其他说明

	[TBD]	

### 其他芯片

[TBD]



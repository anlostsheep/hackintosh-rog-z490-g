[TOC]

# Hackintosh ROG Z490-G

> 华硕 ROG Z490-G + Intel 10700K + AMD Radeon ~~RX560~~ RX6600XT 显卡黑苹果 EFI 制作分享



## 更新日志

### 2022-02-14

1. 更新 OC 引导为 0.7.8-RELEASE 版本
2. 更新显卡为蓝宝石 RX6600XT 超白金，并注入 `PP_PhmSoftPowerPlayTable` 限制显卡频率至 1700MHz - 2200MHz 已解决显卡啸叫问题

# 硬件配置

| CPU  | [Intel i7-10700K](https://www.intel.cn/content/www/cn/zh/products/sku/199335/intel-core-i710700k-processor-16m-cache-up-to-5-10-ghz/specifications.html?wapkw=10700k) |
| ---- | ------------------------------------------------------------ |
| 主板 | [华硕 ROG Z490-G](https://rog.asus.com.cn/motherboards/rog-strix/rog-strix-z490-g-gaming-model/spec) |
| 内存 | [芝奇皇家戟 3600MHz C18 8Gx2](https://item.jd.com/100001749045.html) |
| 显卡 | ~~[迪兰 RX560 X-Serial 4G](http://www.dataland.com.cn/prod_view.aspx?nid=3&typeid=134&id=906)~~ [蓝宝石 RX6600XT](https://www.sapphiretech.com/zh-cn/consumer/nitro-radeon-rx-6600-xt-8g-gddr6_c) |
| 硬盘 | [西数 SN750 500G](https://item.jd.com/100003226990.html) + [铠侠 RC10 1TB](https://item.jd.com/100012956294.html#crumb-wrap) |
| 网卡 | [奋威 FV-T919](https://detail.tmall.com/item.htm?id=569974443985&spm=a230r.7195193.1997079397.6.2cf01358N7YsVb&abbucket=11&skuId=3664842621832) |
| 机箱 | [先马趣造](https://item.jd.com/100016685580.html)            |



## 硬件外观

![IMG_2920](https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/11-29-42-IMG_2920.jpeg)

![IMG_2925](https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/11-30-36-IMG_2925.jpeg)

![IMG_2924](https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/11-31-34-IMG_2924.jpeg)



# 主要功能

## 关于本机

![7G14Gd](https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/11-34-07-7G14Gd.png)



## CPU 睿频

<img src="https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/11-34-40-7G3koF.png" alt="7G3koF" style="zoom:50%;" />



## 核显编解码

![7G3Ei4](https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/11-35-21-7G3Ei4.png)

## 2.5G 网卡

![7G31oD](https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/11-35-59-7G31oD.png)



## WIFI

<img src="https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/11-36-44-7G3wef.png" alt="7G3wef" style="zoom:50%;" />





## 蓝牙

![7G3fmV](https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/11-37-18-7G3fmV.png)

## 独立显卡

> 实际上我使用的是迪兰 RX460 X-Serial 896 流处理器版，刷了蓝宝石 RX560 1024 流处理器的 [VBIOS](https://www.techpowerup.com/vgabios/192320/sapphire-rx560-4096-170419)，原则上只要是显存颗粒是镁光类型的 400/500 系 AMD 显卡都可以刷

![7GGCUU](https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/11-37-58-7GGCUU.png)



## USB 端口定制

> ROG Z490-G 主板后置接口 12 个，1 个 AURA 灯光接口，1 个蓝牙接口，加上机箱上的若干个接口必定超过 15 个接口，需要有所取舍，我的定制接口为删除后置接口上混合接口的两个 USB2.0 接口以及机箱上的 USB2.0 接口(即机箱上仅保留两个 3.0 接口)

<img src="https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/11-39-40-7GGA29.jpg" alt="7GGA29" style="zoom:50%;" />



![7GG9ET](https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/11-40-19-7GG9ET.png)



## iCloud

![7Gz6eK](https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/11-41-02-7Gz6eK.png)



## 隔空投送

![7Gzzyq](https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/11-41-37-7Gzzyq.png)



## iMessage

![7JSkY4](https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/11-42-14-7JSkY4.png)



## 其他无法展示的功能

| 睡眠 | 睡眠正常，定制 USB 端口后即功能正常(如你的机器会出现睡眠即醒的问题可以加入 `SSDT-GPRW.aml` 补丁) |
| ---- | ------------------------------------------------------------ |
| 主题 | 使用定制的主题套装 [BsxOc1](https://github.com/blackosx/BsxOc1) |



## 华硕主板开机或重启卡 F1 问题解决

*问题情况：* 在第一次开机或在 macOS 下重启会出现以下情况

![7JChAf](https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/11-43-17-7JChAf.jpg)

**产生此问题的原因是 Apple RTC 写入了主板不支持或它所没有的区域，从而导致的崩溃与错误**



### 解决方法

1. 在 `BIOS` -> `Boot` 选项中设置忽略 `F1` 提示错误

   > 此做法虽然简单，但会极大地延长了主板开机自检的时间，对于强迫症用户可能无法接受

2. 使用 `OC` 集成的 `DisableRtcChecksum` 配置，在 `Kernel`->`Quirks`->`DisableRtcChecksum`->`True`

   ![DisableRtcChecksum](https://s4.ax1x.com/2022/01/15/7JPjsA.png)

   > 此方法缺点是仅屏蔽区域 0x58-0x59 并且仅在内核级别工作(也就是说有可能你所使用的主板 RCT 不支持的区域不是 0x58-0x59)，如果启用该参数开机卡 `F1` 消失可以使用此方法

3. 使用 `RtcMemoryFixup.kext` 内核补丁，[RtcMemoryFixup](https://github.com/acidanthera/RTCMemoryFixup/releases) 能够在内核级别和固件中通过休眠支持来做到这一点。

   - 最为官方的使用与操作说明：[dortania](https://dortania.github.io/OpenCore-Post-Install/misc/rtc.html#finding-our-bad-rtc-region)

   - 远景接地气式的操作与说明：[关于RTC错误的解决方案](https://bbs.pcbeta.com/viewthread-1879525-1-1.html)

   **重点：** *修改完启动参数后要重启一遍进入 macOS 使启动参数生效再重启一遍验证启动参数是否能解决问题(说人话就是改一次重启参数要重启两遍才能判定改动的重启参数能否解决问题，PS: 我因为只重启一次验证，以为每个区域都有问题，直接重启到怀疑人生)*

   `ROG Z490-G` 的屏蔽区域为: 0x57-0x58

   ![7JPjsA](https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/11-44-19-7JPjsA.png)

## 引导方式

### OpenCore 引导，版本 [0.7.5 RELEASE](https://github.com/acidanthera/OpenCorePkg/releases/tag/0.7.5)

   > 至于为什么没有使用更新的 0.7.6+？是因为官方的 [Dortania](https://dortania.github.io/OpenCore-Install-Guide/) 文档指导只支持到 0.7.5，后面跟随文档升级再升级 OC 版本(主要是懒，不想细看 OC 每个版本升级的 Differences.pdf 文档)

![7tUdyD](https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/11-48-00-7tUdyD.png)

   

### OpenCore 主题

   > 使用不同的主题需对应修改不同的 icon 图标，根据个人喜好制作即可，制作教程可参考远景此篇文章：[自制一个属于自己的oc主题，背景及图标定制教程（新版转换app)](https://bbs.pcbeta.com/viewthread-1883489-1-1.html)

![7ttpkt](https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/12-39-14-7ttpkt.jpg)



## 安装前主板 BIOS 设置

### OC 推荐开启项

- VT-x：CPU的硬件虚拟化技术的一种指令集
  - Advanced -> CPU Configuration -> Intel VT-x Technology -> Supported
- Hyper-Threading：超线程技术
  - Advanced -> CPU Configuration -> Hyper-Threading -> Enabled
- Above 4G Decoding：大于 4G 的编解码空间
  - Advanced -> System Agent(SA) Configuration -> Above 4G Decoding -> Enabled
- 核显开启：
  - Advanced -> System Agent(SA) Configuration -> Graphic Configuration -> iGPU Multi-Monitor -> Enabled
  - Advanced -> System Agent(SA) Configuration -> Graphic Configuration -> DVMT Pre-Allocated -> 64M(或以上)
- USB XHCI Hand-off:
  - Advanced -> USB Configuration -> XHCI Hand-off -> Enabled
- SATA Mode: AHCI
  - Advanced -> PCH Storage Configuration -> SATA Controller(s) -> Enabled
  - Advanced -> PCH Storage Configuration -> SATA Mode Selection -> AHCI



### OC 推荐关闭项

- CSM:
  - Boot -> CSM -> Launch CSM -> Disabled
- Secure Boot:
  - Boot -> Secure Boot ->  OS Type -> Other OS
- Fast Boot:
  - Boot -> Boot Confuguration -> Fast Boot -> Disabled
- VT-d:
  - Advanced -> System Agent(SA) Configuration -> VT-d -> Disabled
- Intel SGX:
  - Advanced -> CPU Configuration -> Software Guard Extensions(SGX) -> Disabled
- CFG Lock:
  - 此主板默认开启，BIOS 中没有此选项



# 安装过程

> 略......



# EFI 食用方式

1. 下载 `RELEASE` 版本中的 EFI-share 文件并改名为 EFI 文件

2. 使用 [Propertree](https://github.com/corpnewt/ProperTree) 或者 [OCAT](https://github.com/ic005k/QtOpenCoreConfig) 打开 EFI/OC/config.plist 文件

3. 使用 [genSMBIOS](https://github.com/corpnewt/GenSMBIOS) 生成机器对应的三码信息放入到如下图样例所示：

   ![7qcMHx](https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/12-44-53-7qcMHx.png)

   又或者使用 OCAT 自动生成三码:

   ![7qc34O](https://gitee.com/anlostsheep/infinity-images/raw/master/uPic/2022/01/27/13-27-41-7qc34O.png)

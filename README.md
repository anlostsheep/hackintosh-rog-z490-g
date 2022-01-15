# Hackintosh ROG Z490-G

> 华硕 ROG Z490-G + Intel 10700K + AMD Radeon RX560 显卡黑苹果 EFI 制作分享



# 硬件配置

| CPU  | [Intel i7-10700K](https://www.intel.cn/content/www/cn/zh/products/sku/199335/intel-core-i710700k-processor-16m-cache-up-to-5-10-ghz/specifications.html?wapkw=10700k) |
| ---- | ------------------------------------------------------------ |
| 主板 | [华硕 ROG Z490-G](https://rog.asus.com.cn/motherboards/rog-strix/rog-strix-z490-g-gaming-model/spec) |
| 内存 | [芝奇皇家戟 3600MHz C18 8Gx2](https://item.jd.com/100001749045.html) |
| 显卡 | [迪兰 RX560 X-Serial 4G](http://www.dataland.com.cn/prod_view.aspx?nid=3&typeid=134&id=906) |
| 硬盘 | [西数 SN750 500G](https://item.jd.com/100003226990.html) + [铠侠 RC10 1TB](https://item.jd.com/100012956294.html#crumb-wrap) |
| 网卡 | [奋威 FV-T919](https://detail.tmall.com/item.htm?id=569974443985&spm=a230r.7195193.1997079397.6.2cf01358N7YsVb&abbucket=11&skuId=3664842621832) |
| 机箱 | [先马趣造](https://item.jd.com/100016685580.html)            |



## 硬件外观

![appearances1](https://s4.ax1x.com/2022/01/15/7G1mb8.png)



![appearance2](https://s4.ax1x.com/2022/01/15/7G10PJ.png)



![appearance3](https://s4.ax1x.com/2022/01/15/7G1rx1.png)



# 主要功能

## 关于本机

<img src="https://s4.ax1x.com/2022/01/15/7G14Gd.png" alt="about" style="zoom:50%;" />



## CPU 睿频

<img src="https://s4.ax1x.com/2022/01/15/7G3koF.png" alt="turbo" style="zoom:50%;" />



## 核显编解码

<img src="https://s4.ax1x.com/2022/01/15/7G3Ei4.png" alt="igpu" style="zoom: 50%;" />



## 2.5G 网卡

![network](https://s4.ax1x.com/2022/01/15/7G31oD.png)



## WIFI

<img src="https://s4.ax1x.com/2022/01/15/7G3wef.png" alt="wifi" style="zoom:50%;" />





## 蓝牙

![bluetooth](https://s4.ax1x.com/2022/01/15/7G3fmV.png)

## 独立显卡

> 实际上我使用的是迪兰 RX460 X-Serial 896 流处理器版，刷了蓝宝石 RX560 1024 流处理器的 [VBIOS](https://www.techpowerup.com/vgabios/192320/sapphire-rx560-4096-170419)，原则上只要是显存颗粒是镁光类型的 400/500 系 AMD 显卡都可以刷

![graphic-card](https://s4.ax1x.com/2022/01/15/7GGCUU.png)



## USB 端口定制

> ROG Z490-G 主板后置接口 12 个，1 个 AURA 灯光接口，1 个蓝牙接口，加上机箱上的若干个接口必定超过 15 个接口，需要有所取舍，我的定制接口为删除后置接口上混合接口的两个 USB2.0 接口以及机箱上的 USB2.0 接口(即机箱上仅保留两个 3.0 接口)

![usb-note](https://s4.ax1x.com/2022/01/15/7GGA29.png)



![usb-hackintosh](https://s4.ax1x.com/2022/01/15/7GG9ET.png)



## iCloud

![icloud](https://s4.ax1x.com/2022/01/15/7Gz6eK.png)



## 隔空投送

![airdrop](https://s4.ax1x.com/2022/01/15/7Gzzyq.png)



## iMessage

![imessage](https://s4.ax1x.com/2022/01/15/7JSkY4.png)



## 其他无法展示的功能

| 睡眠             | 睡眠正常，定制 USB 端口后即功能正常(如你的机器会出现睡眠即醒的问题可以加入 `SSDT-GPRW.aml` 补丁) |
| ---------------- | ------------------------------------------------------------ |
| Apple Watch 解锁 | 在`安全性与隐私`->`通用`中开启使用 Apple Watch 解锁 App 和 Mac |



## 华硕主板开机或重启卡 F1 问题解决

*问题情况：* 在第一次开机或在 macOS 下重启会出现以下情况

![stopF1](https://s4.ax1x.com/2022/01/15/7JChAf.png)

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

   `ROG Z490-G` 的屏蔽区域为: 0x54-0x58

   ![rtc-fix](https://s4.ax1x.com/2022/01/15/7JFd7q.png)

   














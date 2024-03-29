# Surface-Pro6-Opencore

## 前言
- 有一天开车回家的路上，听广播说“某通讯软件偷偷读取Chrome浏览记录”, 突然发现是否可以更换苹果系统避免这个问题。

本来计划使用自己MacBook Pro作为自己的办公机器，然而满多软件不能运行在OSX下，只能看看自己的Surface Pro6，看看是不是可以Hackintosh。

其实很早以前就有安装黑苹果的经历，还记得第一次做IPAD app开发就是在X61下安装的Snow Lepard，那时候还是用的Chameleon 变色龙。

说干就干，百度了半天，补充了相关知识，跟着大佬一步一步学习。

然而有一天手贱，Windows下使用软件做了下系统瘦身，系统就变的奇奇怪怪，花费很多时间都没有解决，只能恢复Windows系统。恢复系统后，顺手就把所有固件也一起更新了下，然后就进去不clover了。


发生了问题，就要多百度和谷歌，在大佬的提示下发现Opencore下已经解决了UEFI导致的问题，重新开始学习OpenCore的相关知识 :)

DisableSecurityPolicy https://github.com/acidanthera/bugtracker/issues/1446 

感谢万能的搜索，发现一个Surface Pro7可以正常使用OC文件，下载下来看看Pro6能否正常使用，于是就有了下面的文字。


## 测试机器：
- Surface 型号: Surface Pro 6 型号 1796 i5

## 版本信息
- UEFI: 235.3440.768.0
- CPU：Intel(R) Core(TM) i5-8250U CPU @ 1.60GHz
- 特别注意平台是：Kaby Lake R
- 内存：8G
- 硬盘驱动器 ：Skhynix BC501 NVMe 256GB  (256 GB)
- OpenCore版本 0.6.7
## 20220615
- 电源显示正常 follow https://github.com/Xiashangning/BigSurface 懒的整合zip了
## 20220106
- 电源按键正常，按三秒显示关机菜单
- 音量+-按键；
## 20210909
- 开启 安全启动secure boot & TPM，去除开机恼人的红底警示
## 20210621 
- update system to os 11.4 ,everything is keep ok.
## 20210319 V1.2
- 解决冷启动黑屏问题，移除多余ssdt文件，修改配置信息。
- 发现主要影响触控板的两个设定为
-   Misc -> Security -> SecureBootModel Disable
-   Misc -> Security -> DmgLoading   Any
- 冷启动不开机为多余的SSDT导致，去除大部分无效SSDT后，冷启动问题解决

## 20210316
- 解决触摸版设置问题 

## 20210309
- 遇到一个问题，第一次启动时，内屏黑屏，HDMI可用，需要进入windows重启一次才能进入系统。 测试过reset nvram没作用。等待有时间进行测试验证时哪些参数设置问题。
- 解决开机后外接需要插拔才显示/休眠唤醒黑屏，在启动参数加上agdpmod=vit9696,pikera igfxonln=1；

## 20210305 V1.1 EFI
- 解决HDMI显示异色问题

## 20210304
- 解决了小米随身Wi-Fi连接网络的问题，需要对kext中的info.plist信息进行修改。
\System\Library\Extensions\RT2870USBWirelessDriver.kext\Contents\Info.plist
小米wifi使用的是联发科的MT7601芯片，它的pid是4106，vid是2717。换算为10进制pid是16646，vid是10007。

<font color=#0000FF  >update 使用一天后，再次开机，DWA160程序crash了，未知异常，后续有机会再看看。</font>

## 20210302
- V1.0 解决外接HDMI问题，未完全解决，显示异色
- V1.1 解决亮度调节功能，去除多余SSDT文件，重新编译config.plist，亮度调节正常
## 20210301
- 上传第一个版本V.10主要解决可以正常进入系统

	- 内屏正常显示
	- 核显驱动正常
	- 声卡驱动正常

-  声音异常，喇叭无声
-  显示异常，显卡驱动19M
经过查询相关资料已经反复测试，修改文档中几个关键节点，目前解决了这两个问题。
OC-显卡参数设置：
显卡还需要在args，参数中，增加 <font color=#FF0000 >-wegnoegpu</font>（关键，要不然显卡驱动异常只有19M，且CPU平台识别异常）

OC-声卡参数设置：声卡alcid=47 声卡

  
## 目前完成： 
1. 内屏显示内建正常；
3. 亮度调节正常；
4. ALC298内建正常；
5. 内置SD卡槽正常；
6. HDMI正常；
7. App Store登陆正常，下载正常；(en0，en1问题）
8. iCloud登陆正常；
9. 触控板正常；
10. 休眠睡眠唤醒正常
11. Siri正常；
12. iMessage正常；
13. Lid正常；
14. 电源按键正常，按三秒显示关键菜单，按一秒开关屏幕；
15. 音量+-按键；
16. 电量显示；
 

## 全球暂时无解：
1. 内置蓝牙+内置WiFi；
2. 摄像头


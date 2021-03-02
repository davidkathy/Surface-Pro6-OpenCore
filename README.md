# Surface-Pro6-Opencore
SurfacePro6-Opencore

--前言
- 有一天开车回家的路上，听广播说“某通讯软件偷偷读取Chrome浏览记录”，突然发现是否可以更换苹果系统避免这个问题。

-本来计划使用自己MacPro作为自己的办公机器，然而满多软件不能运行在OSX下，只能看看自己的SurfacePro6，看看是不是可

以Hackintosh。

其实很早以前就有安装黑苹果的经历，还记得第一次做IPAD app开发就是在X61下安装的Snow Lepard，那时候还是用的Chameleon

 变色龙。
说干就干，百度了半天，补充了相关知识，跟着大佬https://github.com/molie34/Surface-Pro-6-macOS/blob/master/README.md 

手把手把系统安装好了。
然后有一天手贱，windows使用软件做了下系统瘦身，系统就变的奇奇怪怪，花费很多时间都没有解决，只能恢复Windows系统。


恢复系统后，就把所有固件也一起更新了下，然后就进去不clover了。


发生了问题，就要多百度和谷歌，在大佬的提示下发现Opencore下已经解决了UEFI导致的问题，

DisableSecurityPolicy https://github.com/acidanthera/bugtracker/issues/1446又重新开始学校OpenCore ：

）
感谢万能的搜索，发现一个Surface Pro7可以正常使用OC文件，下载下来看看Pro6能否正常使用，就有了下面的文字。



测试机器：
设备名称: DESKTOP-75JFUT3
Surface 型号: Surface Pro 6 型号 1796 i5
版本信息
UEFI: 235.3440.768.0
CPU：Intel(R) Core(TM) i5-8250U CPU @ 1.60GHz
特别注意平台是：Kaby Lake R
内存：8G
硬盘驱动器 ：Skhynix BC501 NVMe 256GB  (256 GB)
OpenCore版本 0.6.6


1，声音异常，喇叭无声
2，显示异常，显卡驱动19M

经过查询相关资料已经反复测试，修改文档中几个关键节点，目前解决了这两个问题。
OC-显卡参数设置：
显卡
显卡还需要在args，参数中，增加 -wegnoegpu（关键，要不然显卡驱动异常只有19M，且CPU平台识别异常）

OC-声卡参数设置：声卡alcid=47 声卡


后续准备解决 电源按键和HDMI显示的问题。


目前完成： 
内屏显示内建正常；
亮度可调节；
ALC298内建正常；
内置SD卡槽正常；
休眠睡眠唤醒正常；
内建假冒en0网卡；
Siri使用正常；
iCloud登陆正常；
还未正常项目：
亮度调节正常
外接HDMI正常，可以同时使用内屏；
App Store登陆正常，下载正常；
iMessage登陆正常
电源按键正常，按三秒显示关键菜单，按一秒开关屏幕
触控板正常
未进行项目：
音量+-按键；
电量显示；
全球暂时无解：
触摸屏、内置蓝牙、内置WiFi、摄像头；


# OpenCore for hasee g8-ca5ns

![product-01](./assets/product-01.jpg)

## 简介

已经完美了🤣。

|       Key        |               Value                |
| :--------------: | :--------------------------------: |
| OpenCore version |            0.9.0 - Mod             |
|  MacOS version   |       Ventura 13.3 (22E252)        |
|   机型开箱参考   | https://post.smzdm.com/p/ax0q7vld/ |

开机界面示例：

![07114713](./assets/07114713.webp)

## Bios 设置

其他的自己摸索下，好像就改了这个，这个机型的 bios 配置很少，网上有 vbios 可以刷，没试过

- 硬盘模式改 AHCI

## 安装说明

- **wifi 需要使用 HeliPort 进行链接，AirportItlwm 需要等待作者更新，目前在 13.3 系统开机需要等好久才能链接到 wifi。**
- 记得换三码，里面没有自带的
- 不要换机型，否则 usb 接口无法使用，需要替换 USBPorts.kext 内 plist 的机型值，你会写代码的话很简单打开改下两个地方就行
- 已经用来写了几天的代码，没啥问题。能开发，这个项目也是在 mac 下系统下传上来的
- Mod 版本的 oc 更新地址：[https://bbs.pcbeta.com/viewthread-1838814-1-1.html](https://bbs.pcbeta.com/viewthread-1838814-1-1.html)

## 硬件

|   Key    |                                                              Value                                                              | Other                                                            |
| :------: | :-----------------------------------------------------------------------------------------------------------------------------: | ---------------------------------------------------------------- |
|   CPU    |                                            Intel(R) Core(TM) i5-10500H CPU @ 2.50GHz                                            | 6 核 12 线程，主频 2.5GHz 睿频 4.5GHz                            |
| 主板型号 |                                                           NH5x_7xDPx                                                            |                                                                  |
|   显卡   |                                                     Intel UHD Graphics 630                                                      |                                                                  |
|  显卡 2  |                                                       英伟达 RTX3060 6GB                                                        | 黑苹果已经屏蔽                                                   |
|   内存   |                                                 Samsung DDR4 2933 MHz 16 GB X 2                                                 | 总共 32GB                                                        |
| 无线网卡 |                                                          Wi-Fi 6 AX200                                                          |                                                                  |
| 有线网卡 |                                    RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller                                    |                                                                  |
|   声卡   |                                                         Realtek ALC293                                                          |                                                                  |
|  显示屏  |                                                                                                                                 | 17.3 寸，100%srgb，1080P 分辨率，300nit 最高亮度，刷新频率 144Hz |
|  触控板  |                                                                ~                                                                |                                                                  |
|   硬盘   |                                              SanDisk Ultra 3D NVMe<br/>PCI-Express                                              |                                                                  |
|   接口   | USB3.0 X2<br/>USB2.0 X1<br/>HDMI X1<br/>RJ45 网口 X1<br/>MiniDP X1<br/>SD 卡槽 X1<br/>电源 X1<br/>Type-C X1<br/>耳机耳麦口各 X1 |                                                                  |

## 正常工作

- CPU 正常睿频
- 英特尔网卡
- 声卡
- 触摸板（支持手势）
- 睡眠
- 核显正常驱动，支持缩放/调节亮度/夜览
- USB 接口完成定制，支持 USB3.0 Type-C

## 存在的问题

- ~~声卡驱动不完美，声卡型号在支持的列表内，但是尝试更换了布局 id，都存在只能同时驱动一个的问题，也就是自带的麦克风和扬声器同时只有一个能工作。暂时不知道怎么解决~~

  ~~个人看法：这个是厄待解决的一个问题，如果作为生产力，有时候会议的时候需要用到，目前只能蓝牙耳机解决~~

  提交的 pr 已经被合并到 applealc 项目内，地址：[https://github.com/acidanthera/AppleALC/pull/837](https://github.com/acidanthera/AppleALC/pull/837)

  **已经解决**

- 电池无法显示通电和断电状态

  ~~个人看法：这个强迫症很难受，虽然是一直插着电使用的，但是看不到电源链接，有些软件会弹出请链接电源使用的提示，这个就很烦，不过还没遇到被阻断的问题~~

  高人指点已经修复。

- ~~触摸板下面左右按键无法使用，好像可以换成其他驱动能使用但是无手势，目前是支持手势的，如果没有鼠标类似滑动的验证码无法拖动~~

  ~~个人看法：这个也比较难受，不过好像可以定制 SSDT 解决下。比较高级，随缘有空研究。~~

  下面两个按键无法作为鼠标左右键使用，但是可以配合触摸板完成拖动动作。例如滑动验证码可以用左键按住触摸板拖动即可。

- ~~无法睡眠(未测试)，但是锁屏后屏幕自动熄屏后无法唤醒，需要重启。~~

  ~~个人看法：我不用睡眠这个功能。使用了 Caffeinated 这个软件防止电脑进入睡眠，不用的时候基本关机。对从 RAM 或者 硬盘中恢复的程序总感觉不干净会出问题。~~

  已经可以睡觉了。可以修复下深度休眠空间啥的。（不能休眠，不知道是 efi 关闭还是系统关闭。没做研究）

  <img src="./assets/iShot_2023-02-07_18.50.57.webp" alt="iShot_2023-02-07_18.50.57" style="zoom:25%;" />

- 无法使用博通网卡支持的隔空投送和随航（是这个吧）之类的功能

  个人看法：不需要这里功能，你需要可以换个网卡。

## 部分系统截图

![iShot_2023-02-07_19.00.14](./assets/iShot_2023-02-07_19.00.14.webp)

程序坞

![iShot_2023-02-07_20.13.57](./assets/iShot_2023-02-07_20.13.57.webp)

| Describe   | screenshot                                                   |
| ---------- | ------------------------------------------------------------ |
| 静音       | <img src="./assets/iShot_2022-12-15_01.07.20.webp" alt="iShot_2022-12-15_01.07.20" style="zoom:25%;" /> |
| 亮度快捷键 | <img src="./assets/iShot_2022-12-15_01.07.31.webp" alt="iShot_2022-12-15_01.07.31" style="zoom:25%;" /> |
| Nvme       | <img src="./assets/iShot_2022-12-15_01.08.12.webp" alt="iShot_2022-12-15_01.08.12" style="zoom: 50%;" /> |
| USB        | <img src="./assets/iShot_2022-12-15_01.08.26.webp" alt="iShot_2022-12-15_01.08.26" style="zoom:50%;" /> |
| 以太网     | <img src="./assets/iShot_2022-12-15_01.08.29.webp" alt="iShot_2022-12-15_01.08.29" style="zoom:50%;" /> |
| 内存       | <img src="./assets/iShot_2022-12-15_01.08.40.webp" alt="iShot_2022-12-15_01.08.40" style="zoom:50%;" /> |
| 显卡       | <img src="./assets/iShot_2022-12-15_01.08.44.webp" alt="iShot_2022-12-15_01.08.44" style="zoom:50%;" /> |
| 摄像头     | <img src="./assets/iShot_2022-12-15_01.08.52.webp" alt="iShot_2022-12-15_01.08.52" style="zoom:50%;" /> |
| 电源       | <img src="./assets/iShot_2023-02-07_19.02.38.webp" style="zoom:50%;" /> |
| 蓝牙       | <img src="./assets/iShot_2022-12-15_01.08.58.webp" alt="iShot_2022-12-15_01.08.58" style="zoom:50%;" /> |
| 读卡器     | <img src="./assets/iShot_2022-12-15_01.09.05.webp" alt="iShot_2022-12-15_01.09.05" style="zoom:50%;" /> |
| 音频       | <img src="./assets/iShot_2022-12-15_01.09.12.webp" alt="iShot_2022-12-15_01.09.12" style="zoom:50%;" /> |
| WIFI       | <img src="./assets/iShot_2022-12-15_01.09.19.webp" alt="iShot_2022-12-15_01.09.19" style="zoom:50%;" /> |

## 部分 efi 截图

| Describe | screenshot                                                   |
| :------: | ------------------------------------------------------------ |
|   ACPI   | ![iShot_2023-02-07_20.09.44](./assets/iShot_2023-02-07_20.10.02.webp) |
|    Dp    | ![iShot_2023-02-07_20.09.53](./assets/iShot_2023-02-07_20.09.53.webp) |
|  Kernel  | ![iShot_2023-02-07_20.09.44](./assets/iShot_2023-02-07_20.09.44.webp) |

## 更新日志

### 2023-04-06

- 更新到 oc 0.9.0

### 2023-03-03

- 尝试使用 mod 版本的 oc

### 2023-02-23

- 增加了 CFGLock 查看工具，需要按住空格显示辅助工具
- 默认隐藏辅助工具，按住空格显示

关于 cfg lock 我已经在 Windows 解锁了。教程我会放出来。

### 2023-02-17 更新 OC 到 0.8.9 

- 更新 OC 到 0.8.9
- 更新显卡驱动

## 参考

- [Clevo-NH50-NH70-Hackintosh](https://github.com/MichaelPan1026/Clevo-NH50-NH70-Hackintosh)

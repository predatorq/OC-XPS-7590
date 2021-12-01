# OC-XPS-7590

XPS 7590 with OpenCore

FORK FROM [Gorquan's Work](https://github.com/gorquan/OC-XPS-7590)

感谢大佬的付出，原项目已经十分完善。

### 此项目与原项目的区别

- 原项目opencore版本到0.7.2，在八月后疑似停更。此项目会持续更新opencore以及各kext，直到我换电脑。

- 原仓库更换为博通网卡，因为现有itlwm项目已经较为完善，所以本项目使用Intel网卡。

- Readme相较原项目按照个人喜好进行删减，删除了部分自己没有遇到的问题的解决方法。

- 我现有的电脑为xps7590的最低配版，并不含有独立显卡，与原项目主的配置也有不同，但EFI一般来说可以通用。

### 电脑与原装出厂的区别

- 更换了内存（原装的2条4G实在不够使用）

### 引导版本

OpenCore: **0.7.6**

MacOS:  11.4  **11.6.1**

以上两个系统版本经过测试可用，其余请自行尝试。

如果使用monterey可能需要更新[itlwm](https://github.com/OpenIntelWireless/itlwm)

### 配置信息

| Key   | Value                         |
| ----- | ----------------------------- |
| 型号    | XPS-7590                      |
| CPU   | Intel Core i5 9300H           |
| 核芯显卡  | Intel Graphics UHD 630        |
| 内建显示屏 | 15.6" 1080p **非触屏**           |
| 内存    | 更换为英睿达8G 2条                   |
| 固态硬盘  | SSDPEMKF512G8 NVMe INTEL 512G |
| 板载声卡  | Realtek ALC298                |
| 无限网卡  | 原装Killer1650                  |

### 使用前注意

- **请先参考该文章：[XPS 7590 1.6.0 UEFI: unlock undervolting and remove CFG lock](https://www.reddit.com/r/Dell/comments/fzv599/xps_7590_160_uefi_unlock_undervolting_and_remove/)，对CFG Lock进行解锁再使用该OpenCore！**
- 目前仅为完善macOS，可能会导致Windows出现不稳定情况。
- 与kext相关的内容添加会同时同步到其他Opencore版本的config文件中，但**不保证可用性**，请自行测试。**建议使用仓库最新版**
- 使用前请先**更新序列号**，以免被苹果拉黑账号。
- 请各基于本仓库的定制版，**注明来源并更新机器序列号**再进行使用，谢谢！

### 工作情况

- CPU：
  - 正常工作
  - 正常变频,最低频率800MHz
  - 温度正常
- 板载声卡：
  - 正常工作
  - 支持耳机、内置扬声器和HDMI音频输出
  - 支持内建麦克风
- 核芯显卡：
  - 正常工作
  - 支持HDMI输出
- 内建显示屏：
  - 正常工作
- 蓝牙：
  - 正常工作
  - 能够与其他设备正常连接
- 电池：
  - 正常工作
  - 续航时间可以长达5小时（电池健康情况下）
- 无线网卡：
  - 正常工作
  - 隔空投送、随航因为Intel网卡限制无法使用
- 键盘：
  - 正常工作
  - 键盘灯能够正常显示
  - 快捷键正常工作
- 触控板：
  - 正常工作
- 睡眠：
  - 正常工作
  - 盒盖睡眠正常工作
- 读卡器：
  - 正常工作
- USB
  - 支持安卓手机USB网络共享功能

### 存在问题的设备

- 读卡器
  - 无法使用只读模式（内存卡加锁）

### 驱动情况

- 全部驱动为最新

### 引导更新日志

- 2021.12.1
  - fork from原项目
  - 升级opencore至0.7.6
  - 升级kext

### 引导补充说明

- 由于采用了PNP0C0D睡眠，因此Fn+Insert在外接HDMI情况下将关闭内屏而不是睡眠，当不外接HDMI时电脑将进行睡眠

### 进入系统后优化

- 对于睡眠部分，请参考睡眠设置

### 睡眠处理

1. 检查hibernatemode是否为0或3

```shell
pmset -g | grep hibernatemode
```

2. 在终端执行以下命令

```shell
sudo pmset -a standby 0
sudo pmset -a proximitywake 0
sudo pmset -a hibernatemode 3 # 如果hibernatemode 不为3或0 执行此条命令
sudo pmset -a tcpkeepalive 0 # 如果仍然睡不着可以尝试一下睡眠期间断开网络连接
```

3. 除了“当显示器关闭时，防止电脑自动进入睡眠”是可选的外，请关闭设置-节能器里的所有其他选项。

### 感谢

- Apple
- 各位Kext开发者
- 原项目作者[@Gorquan](https://github.com/gorquan)
- [@Acidanthera](https://github.com/acidanthera)
- [@daliansky](https://github.com/daliansky)
- [@geek5nan](https://github.com/geek5nan/Hackintosh-XPS7590)
- [@Dracay](https://github.com/Dracay)
- [@tiger511](https://github.com/tiger511)
- [@shadowed87](https://github.com/shadowed87)
- [@Pinming](https://github.com/Pinming)
- [@tctien342](https://github.com/tctien342)
- [@xxxzc](https://github.com/xxxzc)
- [@romancin](https://github.com/romancin)
- [@cholonam](https://github.com/cholonam)
- [@illusion899](https://github.com/illusion899)

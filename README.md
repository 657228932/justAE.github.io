# 小米笔记本Pro 2017 & 2018 黑苹果

## 电脑配置

| 规格     | 详细信息                                     |
| -------- | ---------------------------------------- |
| 电脑型号 | 神舟战神笔记本电脑z7-kp7gs(模具为蓝天clevo N857HP6)             |
| 处理器   | 英特尔 酷睿 i7-7700hq 处理器             |
| 内存     | 16GB 镁光 DDR4 2400MHz                 |
| 硬盘     | 镁光 NVMe固态硬盘 512                   |
| 集成显卡 | 英特尔 UHD 图形620                            |
| 显示器   | 京东方 NV156FHM-N61 FHD 1920x1080 (15.6 英寸) |
| 声卡     | 瑞昱 ALC298 (节点:30/99)                     |
| 网卡     | 英特尔 无线 8265                              |
| 读卡器   | 瑞昱 RTS5129/RTS5250S                      |


## Clover版本的目前情况

- <b>有线网在macOS 10.15下无法工作，需要帮助</b>
- 如果升级到macOS 10.15，需要更新[USB无线网卡驱动](https://github.com/chris1111/Wireless-USB-Adapter-Clover/releases)
  - 如果不是macOS 10.15，也推荐更新上述驱动
- 独立显卡无法工作，因为macOS不支持Optimus技术
  - 使用了 [SSDT-DDGPU](EFI/CLOVER/ACPI/patched/SSDT-DDGPU.dsl) 来禁用它以节省电量
- 指纹传感器无法工作
  - 使用了[SSDT-USB](EFI/CLOVER/ACPI/patched/SSDT-USB.dsl)来禁用它以节省电量
- ~~英特尔蓝牙只有在从Windows热重启后有效~~
  - ~~阅读[蓝牙解决方案](https://github.com/daliansky/XiaoMi-Pro/wiki/蓝牙解决方案)~~
- 英特尔无线网卡无法工作
  - 使用了[SSDT-DRP08](EFI/CLOVER/ACPI/patched/SSDT-DRP08.dsl)来禁用它以节省电量
  - 购买USB网卡或者支持的内置网卡
- 瑞昱USB SD读卡器无法工作
  - 使用了[SSDT-USB](EFI/CLOVER/ACPI/patched/SSDT-USB.dsl)来禁用它以节省电量
- 其他都工作正常


## OpenCore版本的目前情况

- 和[Clover版本的目前情况](#clover版本的目前情况)小节基本一致
- 没有主题

需要更多测试。。。


## 安装

### 首次安装

- 请参考详细的安装教程[【老司机引路】小米笔记本pro Win10+黑苹果macOS 10.13.6双系统](http://www.miui.com/thread-11363672-1-1.html)，视频教程[小米笔记本Pro(win10+Mojave10.14.3)双系统过程以及一些问题解答](http://www.bilibili.com/video/av42261432?share_medium=android&share_source=copy_link&bbid=bVk_DmoLaV48Wj4Pcw9zinfoc&ts=1555066114848)。
- 如果安装过程中触控板失效，请在安装前插上有线鼠标或者无线鼠标发射器。安装完成后打开 `终端.app` 并运行 `sudo kextcache -i /`，等待进程结束重启即可使用触控板。
- 完整的EFI附件请访问 [releases](https://github.com/daliansky/XiaoMi-Pro/releases) 页面。
 - 如果是日常使用，请不要克隆或者下载master分支。
 
 <img src="img/donot_Clone_or_Download.jpg" width="300px" alt="donot_clone_or_download">
 <img src="img/get_Release.jpg" width="300px" alt="get_release">
 
 ### 更新
 
- 完整替换 `BOOT` 和 `CLOVER`(或 `OC`)文件夹。首先删除他们，然后从[release 包里](https://github.com/daliansky/XiaoMi-Pro/releases)拷贝新的。
- 你也可以在终端输入以下命令来更新EFI：

```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/daliansky/XiaoMi-Pro-Hackintosh/master/install_cn.sh)"
```


## 常见问题解答

### 我的设备被 `查找我的Mac` 锁住了，无法开机，怎么办？

在Clover开机界面按下 `Fn+F11`。然后Clover会刷新 `nvram.plist` 并移除锁定信息。

### 我开启了 `文件保险箱`，开机时找不到macOS启动项，怎么办？

一般情况下不推荐开启 `文件保险箱`。你可以在Clover开机界面时按下Fn + F3，然后选择下方小字含有 `FileVault` 的苹果图标。进入系统后关闭 `文件保险箱`。

### 在升级过程中显示器黑屏并且机子无反应

如果显示器持续黑屏并且无反应超过五分钟，请强制重启电脑(长按电源键)并选择 `Boot macOS Install from ~` 启动项。

### 我的触控板升级系统后无法使用。

你需要在每次更新系统后重建缓存。运行 `Kext Utility.app` 或者在 `终端.app` 输入 `sudo kextcache -i /`，然后重启。如果触控板还是失效，试试按下F9键。

### 我无法通过Clover进入Windows/Linux，但是可以通过按F12，然后选择系统进入。

很多人使用了新版 `AptioMemoryFix.efi` 后无法正常进入Windows/Linux系统。一个解决方案是先删除 `/CLOVER/drivers/UEFI/` 里的 `AptioMemoryFix.efi`，然后替换进[#93](https://github.com/daliansky/XiaoMi-Pro/issues/93)提供的旧版`AptioMemoryFix.efi`。

同时确保 `沙盒`(Sandbox) 和 `Hyper-V` 功能关闭。






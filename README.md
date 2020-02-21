# 神舟笔记本z7-kp7gs黑苹果

## 电脑配置

| 规格     | 详细信息                                     |
| -------- | ---------------------------------------- |
| 电脑型号 | 神舟战神笔记本电脑z7-kp7gs(模具为蓝天clevo N857HP6)             |
| 处理器   | 英特尔 酷睿 i7-7700hq 处理器             |
| 内存     | 16GB 镁光 DDR4 2400MHz                 |
| 硬盘     | 镁光 NVMe固态硬盘 512GB+ 西部数据 sata3 绿盘 1T                   |
| 集成显卡 | 英特尔 HD 630                            |
| 独立显卡 | 英伟达 GTX 1060 6GB                            |
| 显示器   | 京东方 NV156FHM-N61 FHD 1920x1080 (15.6 英寸) |
| 声卡     | 瑞昱 ALC269 (节点:18)                     |
| 无线网卡     | 英特尔 无线 3160AC                              |
| 有线网卡     | Realtek RTL8168/8111 PCI-E Gigabit Ethernet Adapter PCI                             |
| 读卡器   | 瑞昱 RTS5129/RTS5250S                      |


## Clover版本的目前情况

- <b>无线网卡在macOS 10.15下无法工作，需要更换1820A</b>
- 独立显卡无法工作，因为macOS不支持Optimus技术
  - 使用了 [SSDT-DDGPU](EFI/CLOVER/ACPI/patched/SSDT-DDGPU.dsl) 来禁用它以节省电量
  



## OpenCore版本的目前情况

-未使用
需要更多测试。。。






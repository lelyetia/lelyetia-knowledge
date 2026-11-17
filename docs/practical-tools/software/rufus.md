# Rufus：USB 启动盘制作<sup>*</sup>

## 用途与入口

Rufus 用于格式化 USB 存储设备，并将可引导的系统镜像写入 USB 启动盘。可以用它准备 Windows、Linux、Clonezilla 或 GParted Live 的启动介质。[^rufus]

- [官方网站与下载入口](https://rufus.ie/zh/)
- [官方 GitHub 仓库](https://github.com/pbatard/rufus)
- [官方常见问题](https://github.com/pbatard/rufus/wiki/FAQ)

Rufus 运行在 Windows 上。若制作启动盘的电脑正在使用 Ubuntu，应选择对应平台的镜像写入工具；目标启动盘可以用于其他系统，并不代表 Rufus 自身能够在这些系统上运行。[^faq]

## 制作启动盘的基本流程

1. 从目标软件或操作系统的官方网站下载镜像文件。
2. 插入用于制作启动盘的 USB 设备，并备份其中的文件；写入过程会覆盖目标设备上的现有数据。
3. 打开 Rufus，在“设备”中按名称和容量核对目标 USB 设备。
4. 在“引导类型选择”中选择镜像，再检查分区类型、目标系统与文件系统等设置。
5. 点击“开始”，阅读软件提示并确认后等待写入完成。
6. 安全移除启动盘，在目标电脑的一次性启动菜单中选择对应 USB 启动项。

写入之前要分清“镜像文件”和“要被写入的 USB 设备”。普通文件复制通常不能完成启动盘所需的引导布局，应使用镜像写入流程。[^rufus][^repository]

## 分区类型、启动方式与写入模式

| 设置 | 理解方式 |
| --- | --- |
| 分区类型 | 启动盘自身采用的 GPT 或 MBR 布局 |
| 目标系统 | 希望启动的固件环境，例如 UEFI 或传统 BIOS |
| ISO / DD 模式 | 镜像支持时可选择的两种写入方式，具体按镜像项目说明与 Rufus 提示选择 |

常见 Windows 安装盘使用 GPT 与 UEFI 配合，传统 BIOS 安装介质通常使用 MBR；Linux Live 镜像的可用组合还取决于镜像自身。不要为了让启动盘出现，就直接更改现有系统的固件启动方式。

Rufus 对支持两种写入方式的混合镜像通常优先提供 ISO 模式。若项目文档要求 DD，或 ISO 模式确实无法正常启动，可按照官方说明重新制作。[^faq]

## 与磁盘维护工具配合

| 要完成的事情 | 准备的镜像 | 启动后使用的工具 |
| --- | --- | --- |
| 更换硬盘并迁移现有系统 | Clonezilla Live | [Clonezilla](clonezilla.md) |
| 整理分区或为 Windows 预留空间 | GParted Live | [GParted](gparted.md) |
| 安装或修复 Windows | 对应版本的 Windows 官方安装介质 | Windows 安装程序或恢复环境 |

Rufus 完成的是启动介质制作。进入 Live 环境后的源盘选择、分区调整和系统修复，需要按相应工具的流程继续处理。

## 常见排查方向

- 启动菜单找不到 USB：先核对 USB 连接、镜像架构及启动盘与固件模式是否匹配。
- 能启动但 Live 系统运行异常：查看镜像项目的说明；启动盘写入成功不等于其中的软件一定兼容目标硬件。
- ISO 写入报错：保留 Rufus 日志，并检查镜像文件与 USB 设备。[^faq]

## 参考资料

[^rufus]: Rufus. [官方中文网站](https://rufus.ie/zh/)。访问日期：2026-11-11。
[^faq]: Rufus. [FAQ](https://github.com/pbatard/rufus/wiki/FAQ)。访问日期：2026-11-11。
[^repository]: Rufus. [官方项目与功能说明](https://github.com/pbatard/rufus)。访问日期：2026-11-11。

## 版本记录 {#version-history}

| 版本号 | 更新日期 | 更新概述 |
| --- | --- | --- |
| v0.1.0 | 2026-11-11 | 整理 Rufus 的启动盘制作流程、参数含义及与磁盘维护工具的配合方式。 |

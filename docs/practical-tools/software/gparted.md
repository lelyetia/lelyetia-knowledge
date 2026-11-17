# GParted：分区管理与 Windows 分区维护<sup>*</sup>

## 用途与入口

GParted 是图形化的磁盘分区编辑器，可以创建、调整、移动、复制及检查分区。修改正在使用的系统盘时，通常从 GParted Live 启动，以便在分区未被系统占用的环境中操作。[^gparted]

- [官方网站](https://gparted.org/)
- [GParted Live 下载与使用入口](https://gparted.org/livecd.php)
- [完整使用手册](https://gparted.org/display-doc.php?name=help-manual)

## 先区分三个层次

| 层次 | 需要确认的内容 |
| --- | --- |
| 磁盘或 RAID 逻辑设备 | 当前操作的设备、容量与已有数据是否正确 |
| 分区布局 | 分区的起止位置、大小及相邻未分配空间 |
| 分区内的文件系统 | NTFS、ext4 等类型，以及是否支持目标操作 |

官方功能表列出了硬件 RAID、主板 BIOS RAID 与 Linux 软件 RAID 设备。实际使用时，应先确认 Live 环境已经正确识别阵列设备，再操作其上的分区；分区管理不能替代 RAID 控制器或阵列本身的配置。[^features]

## 创建与调整分区

1. 备份重要数据，进入 GParted Live，并核对设备选择框中的目标磁盘。
2. 根据已有分区、卷标和文件系统确认空间用途。为新系统创建分区时，选择确实未使用的未分配空间。
3. 选择创建分区，或对已有分区使用 `Resize/Move`，检查容量和前后空闲空间。
4. 核对待执行操作队列，再应用本次布局修改，等待完成后检查结果。

多数分区修改需要先卸载分区；扩容通常需要目标分区旁边有连续的未分配空间。已有数据的整盘不能通过“新建分区表”来腾空间，该操作会重写磁盘的分区布局。[^manual]

## Windows 与 RAID 场景

在已识别的 RAID 逻辑设备上为 Windows 整理空间时，应先记录现有布局，再判断哪些空间可用。已有 Windows 系统的 EFI、恢复分区与数据分区可能承担不同作用，不能只按大小判断能否删除。

修改 NTFS 系统分区前应完整关闭 Windows；处于休眠、未正常关闭或已有文件系统错误的分区，需要先处理其状态。操作是否可用以 `View → File System Support` 和当前版本的支持情况为准。[^manual]

## “检查分区”与“修复启动”的区别

| 问题 | 处理方向 |
| --- | --- |
| 分区容量或布局不合适 | 调整分区布局 |
| 文件系统存在问题 | 使用支持的 `Partition → Check`；NTFS 的深入检查可回到 Windows 处理 |
| 文件仍在，但 Windows 无法启动 | 检查启动模式及引导环境，必要时使用 Windows 安装或恢复介质 |

GParted 的 `Check` 会尝试检查并修复文件系统问题；它不等于重建 Windows 的 EFI 引导文件或 BCD。官方 FAQ 将 Windows 启动问题单独归入恢复环境处理。[^manual][^faq]

若操作按钮灰色不可选，优先检查分区是否挂载，以及当前环境是否具备对应文件系统工具。遇到 BitLocker 加密分区时，应先核对支持范围，不能直接套用普通 NTFS 分区的调整流程。[^features][^faq]

## 参考资料

[^gparted]: GParted. [项目介绍](https://gparted.org/)；[GParted Live](https://gparted.org/livecd.php)。访问日期：2026-11-11。
[^features]: GParted. [设备与文件系统功能支持表](https://gparted.org/features.php)。访问日期：2026-11-11。
[^manual]: GParted. [GParted Manual](https://gparted.org/display-doc.php?name=help-manual)。访问日期：2026-11-11。
[^faq]: GParted. [Frequently Asked Questions](https://gparted.org/faq.php)。访问日期：2026-11-11。

## 版本记录 {#version-history}

| 版本号 | 更新日期 | 更新概述 |
| --- | --- | --- |
| v0.1.0 | 2026-11-11 | 整理分区管理、RAID 设备识别与 Windows 分区维护的基本方法。 |

# Clonezilla：磁盘克隆与迁移<sup>*</sup>

## 用途与入口

Clonezilla（再生龙）是一款开源的磁盘与分区镜像、克隆工具，适合更换硬盘、迁移已有系统，以及制作可还原的整盘备份。单机操作通常使用从 USB 启动的 Clonezilla Live。[^clonezilla]

- [官方网站](https://clonezilla.org/)
- [下载入口](https://clonezilla.org/downloads.php)
- [与 GParted 的分工](gparted.md)：Clonezilla 负责迁移数据，GParted 负责整理分区布局。

## 两种工作模式

| 模式 | 数据流向 | 常见用途 |
| --- | --- | --- |
| `device-device` | 源磁盘或分区 → 目标磁盘或分区 | 两块硬盘同时连接时直接克隆 |
| `device-image` | 磁盘或分区 ↔ 镜像文件 | 先保存备份，再在需要时还原 |

官方教程中的 `savedisk` 用于保存整盘镜像，`restoredisk` 用于还原整盘镜像；整盘对拷使用 `disk_to_local_disk`。选择入口前，先确定这次要直接迁移，还是先保存一份镜像。[^live-docs]

## 整盘迁移的基本流程

以下按源盘与目标盘均已连接、目标盘容量不小于源盘的常见情况整理。目标盘会被覆盖，应提前备份其中仍需保留的数据。[^disk-clone]

1. 下载 Clonezilla Live，并准备独立启动盘；在 Windows 下可参考 [Rufus 笔记](rufus.md)。
2. 从启动盘进入 Clonezilla Live，选择语言与键盘布局，启动 Clonezilla。
3. 选择 `device-device`，使用 `Beginner` 模式，再选择 `disk_to_local_disk`。
4. 按型号、容量和序列号核对源盘与目标盘，不能只凭 `/dev/sda`、`/dev/sdb` 的顺序判断。
5. 检查软件给出的操作摘要，确认复制方向后开始克隆。
6. 完成后关机，首次验证时只连接或只启用目标盘，检查系统能否启动、文件是否完整。

源盘与克隆盘可能具有相同的文件系统 UUID。官方教程建议首次启动验证时只保留其中一块，避免系统识别到重复的文件系统。[^disk-clone]

## 迁移后的空间与验证

从小盘迁往大盘后，需要检查分区是否已经利用新增容量。若仍有未分配空间，可在确认系统与数据正常后，再使用 GParted 调整兼容文件系统的分区大小。

整盘迁移后，先验证目标盘独立启动、常用程序、关键文件与分区容量，再决定如何处理源盘。确认迁移成功前，保留源盘作为回退依据。

## 参考资料

[^clonezilla]: Clonezilla. [Clonezilla Live 介绍](https://clonezilla.org/clonezilla-live.php)。访问日期：2026-11-11。
[^live-docs]: Clonezilla. [Clonezilla Live 操作教程](https://clonezilla.org/clonezilla-live-doc.php)。访问日期：2026-11-11。
[^disk-clone]: Clonezilla. [Disk to disk clone](https://clonezilla.org/show-live-doc-content.php?form=MG0AV3&topic=clonezilla-live/doc/03_Disk_to_disk_clone)。访问日期：2026-11-11。

## 版本记录 {#version-history}

| 版本号 | 更新日期 | 更新概述 |
| --- | --- | --- |
| v0.1.0 | 2026-11-11 | 整理 Clonezilla 的工作模式、整盘迁移流程与迁移后验证。 |

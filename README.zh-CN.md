# Madis Peek 3D

[English](README.md) | [简体中文](README.zh-CN.md)

Madis Peek 3D 是一款基于 Tauri 的桌面三维模型预览与轻量网格编辑软件，可用于查看、检查、精简和调整三角网格。

官方网站：<https://madis.top>

## 下载

官方桌面安装包通过本仓库的 [GitHub Releases](https://github.com/MadisTop/madis-peek-3d/releases) 发布，并镜像到 [Gitee 发行版](https://gitee.com/madis/madis-peek-3d/releases)。测试阶段两个发布仓库可能保持私有，请以所选 Release 页面实际显示的资产为准。

测试版本会标记为 **Pre-release**。Release 提供 `SHA256SUMS.txt` 时，请在安装前校验下载文件。

## 主要功能

- 导入 OBJ、STL 和 GLB 2.0 三角网格
- 解码使用 `KHR_draco_mesh_compression` 的 GLB 网格
- 流畅旋转、平移、缩放、适应视图、原生文件对话框、启动文件和拖放操作
- 界面支持简体中文和英文，默认跟随操作系统语言，可在“视图 → 语言”中切换并持久化偏好
- 通过“视图”菜单显示或隐藏工具栏、属性面板和状态栏，并在本机保存选择
- 实体、透明度、线框、参考网格、坐标轴，以及视口内三维包围盒和长宽高尺寸线标注
- 文件名、完整路径、原文件大小、顶点数、三角面数、包围尺寸和按需渲染耗时显示
- 通过坐标精度精简网格，并同步比较原始模型与 0～7 位小数结果
- 轻量网格编辑：移动与合并顶点、顶点/边中点/XYZ 轴向吸附、选择与删除面、退化面清理和单步撤销
- 导出 OBJ 和二进制 STL、保存视口截图，并提供尝试 Draco 压缩的 GLB 导出路径
- 自定义无边框桌面窗口，应用界面自动跟随系统浅色/深色模式，视口背景可独立选择
- 普通更新可在后台静默下载并于退出时安装；强制更新可立即检查并安装，失败时可继续使用官方下载页

## 格式限制

Madis Peek 3D 会把导入内容转换为一个可编辑三角网格。GLB 中的多个网格在应用节点世界变换后会被扁平化；基础颜色会尽量保留，但纹理、完整材质、动画、蒙皮、Morph Target、相机、灯光和原始场景层级不会进行无损往返保留。

Draco 压缩 GLB 导出仍需在每个目标平台持续进行运行时验证。请保留生产模型的原始文件，不要把本软件导出结果作为唯一副本。

## 快捷键

| 快捷键                 | 功能                                  |
| ---------------------- | ------------------------------------- |
| `Ctrl/Cmd+O`           | 打开模型                              |
| `Ctrl/Cmd+S`           | 打开模型导出面板                      |
| `Ctrl/Cmd+P`           | 保存当前视口截图                      |
| `Ctrl/Cmd+Z`           | 单步撤销 / 在最近两份网格快照之间切换 |
| `E`                    | 切换编辑模式                          |
| `F`                    | 适应视图                              |
| `R`                    | 重置相机                              |
| `G`                    | 切换参考网格                          |
| `A`                    | 切换坐标轴                            |
| `F5`                   | 清除当前模型                          |
| `Delete` / `Backspace` | 编辑模式下删除选中三角面              |
| `Esc`                  | 关闭弹窗或取消当前顶点拖动            |

表中的 `Cmd` 表示 macOS Command 键，Windows 和 Linux 使用 `Ctrl`。平台匹配逻辑已有单元测试覆盖，真实键盘操作仍属于各平台安装包回归范围。

## 平台与信任状态

构建配置以 Windows x64、Linux x64、macOS Intel 和 macOS Apple Silicon 为目标。安装包格式以每个 Release 实际生成的资产为准，四个平台的真实安装与跨版本在线升级仍需完成端到端验证。

Tauri Updater 产物和 `latest.json` 使用 Minisign 保护。它用于验证更新载荷，不代表操作系统认可的平台代码签名身份。

- stable Linux Release 要求 AppImage 和 RPM 具备原生 OpenPGP 签名，并随 Release 提供公钥和完整指纹。DEB 当前没有独立原生包签名，仅使用 SHA-256 与 Updater Minisign 校验；test Release 在缺少签名 Secrets 时可能明确标注本次跳过 Linux 原生签名。
- 普通 GitHub/Gitee Release 中的 Windows NSIS 和 MSI 没有 Authenticode，系统仍可能显示未知发布者或 SmartScreen 警告。
- Microsoft Store 是独立渠道。专用工作流生成未签名 MSIX 提交包，该输入包不会上传普通 Release；通过 Partner Center 审核后，商店下发版本由微软签名。
- macOS 当前仅使用 ad-hoc 签名，不包含 Developer ID 身份，也没有 Apple 公证。

安装前请阅读对应 Release notes，核对 `SHA256SUMS.txt`；Release 提供 Linux 签名公钥与指纹时，也请一并核验。

## 问题反馈

安装或使用过程中遇到问题，可以通过本仓库的 Issues 页面反馈。请提供操作系统、软件版本、模型格式、近似顶点/三角面数量和可复现步骤；未经授权请勿上传私有或未公开的三维模型。

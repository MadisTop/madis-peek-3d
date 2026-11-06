# Madis Peek 3D

[English](README.md) | [简体中文](README.zh-CN.md)

Madis Peek 3D 是一款基于 Tauri 的桌面三维模型预览与轻量网格编辑软件，可用于查看、检查、精简和调整三角网格。

官方网站：<https://madis.top>

## 下载

官方桌面安装包通过本仓库的 [GitHub Releases](https://github.com/MadisTop/madis-peek-3d/releases) 发布，并镜像到 [Gitee 发行版](https://gitee.com/madis/madis-peek-3d/releases)。请以所选 Release 页面实际显示的安装包为准。

测试版本会标记为 **Pre-release**。Release 提供 `SHA256SUMS.txt` 时，请在安装前校验下载文件。

## 主要功能

- 导入 OBJ、STL 和 GLB 2.0 三角网格
- 解码使用 `KHR_draco_mesh_compression` 的 GLB 网格
- 流畅旋转、平移、缩放、适应视图、原生文件对话框、启动文件和拖放操作
- 界面支持简体中文和英文，默认跟随操作系统语言，可在“视图 → 语言”中切换并持久化偏好
- 通过“视图”菜单在当前会话显示或隐藏工具栏、属性面板和状态栏
- 实体、透明度、线框、参考网格、坐标轴，以及视口内三维包围盒和长宽高尺寸线标注
- 文件名、完整路径、原文件大小、顶点数、三角面数、包围尺寸显示；开发模式还可显示按需渲染耗时
- 通过坐标精度精简网格，并同步比较原始模型与 0～7 位小数结果
- 轻量网格编辑：移动与合并顶点、顶点/边中点/XYZ 轴向吸附、选择与删除面、退化面清理和单步撤销
- 导出 OBJ 和二进制 STL、保存视口截图，并提供尝试 Draco 压缩的 GLB 导出路径
- 自定义无边框桌面窗口，应用主题可选择跟随系统、浅色或深色，视口背景可独立选择
- 普通更新可在后台静默下载并于退出时安装；强制更新可立即检查并安装，失败时可继续使用官方下载页

## 格式限制

Madis Peek 3D 会把导入内容转换为一个可编辑三角网格。GLB 中的多个网格在应用节点世界变换后会被扁平化；基础颜色会尽量保留，但纹理、完整材质、动画、蒙皮、Morph Target、相机、灯光和原始场景层级不会进行无损往返保留。

GLB 导出依赖 Draco 编码器与运行环境；编码失败时会报告错误，不会自动降级为未压缩 GLB。请保留生产模型的原始文件，不要把本软件导出结果作为唯一副本。

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

表中的 `Cmd` 表示 macOS Command 键，Windows 和 Linux 使用 `Ctrl`。

## 支持平台

支持 Windows x64、Linux x64、macOS Intel 与 Apple Silicon 目标。安装包格式与可用版本以所选 Release 的下载列表为准。

## 安装安全与隐私

请从官方发布页选择与操作系统和处理器架构匹配的安装包，阅读该版本的使用注意事项，并在提供校验清单时核对 `SHA256SUMS.txt`。仅凭文件名、下载成功或校验值相符不能替代来源与签名身份核验。

- Updater 的 Minisign 用于验证更新载荷，不代表 Windows Authenticode、macOS Developer ID/公证或 Linux 包签名，也不保证操作系统不会显示安全提示。
- Windows 未知发布者、SmartScreen 或 macOS 安全提示出现时，应先核对下载来源和系统显示的签名身份，不要为安装而全局关闭系统防护。
- Linux 发布页提供 OpenPGP 公钥与完整指纹时，应从可信渠道核对指纹后验签；不同包格式的校验方式不能互相替代。
- Microsoft Store 等独立渠道的发布者身份与安装权限，以相应商店实际展示的信息为准。
- 请保留原始模型副本，并只打开可信来源的文件。反馈问题前请移除本机路径、个人信息和模型中的敏感内容；未经授权不要上传私有模型。

## 问题反馈

安装或使用过程中遇到问题，可以通过本仓库的 Issues 页面反馈。请提供操作系统、软件版本、模型格式、近似顶点/三角面数量和可复现步骤；未经授权请勿上传私有或未公开的三维模型。

## 安装目录、用户数据与便携模式

Windows NSIS 与 MSI 新装默认安装到 `%LOCALAPPDATA%\Programs\Madis\Peek3D`；升级时优先恢复仍含本产品程序的合法安装目录。应用 identifier 保持 `top.madis.peek3d`。同类型安装器支持恢复合法位置；不支持 MSI/NSIS 直接跨类型覆盖，切换前请先卸载原类型并保留数据，再安装新类型，不将此流程视为已验证的跨类型升级。

安装模式的原生用户数据根目录：

- Windows：`%LOCALAPPDATA%\Madis\Peek3D`。
- macOS：`~/Library/Application Support/Madis/Peek3D`。
- Linux：有效的绝对 `XDG_DATA_HOME` 下的 `Madis/Peek3D`；未设置、为空或为相对路径时使用 `~/.local/share/Madis/Peek3D`。

根目录下，`Data` 为持久内容，`State` 为不可当作缓存随意清理的持久状态，`Cache` 为可再生缓存，`WebView` 为 Windows/Linux 浏览器 profile（包括 localStorage），`Logs` 按需创建。Windows WebView2 的实际 profile 子层是 `WebView/EBWebView`（例如 localStorage 在其 Default 子目录内）。可信时间、策略序号和已验签策略位于 `State/version-policy`；删除这些文件会损害本地防回退历史，不能当作日常“清缓存”。macOS 的 WKWebView profile 由系统管理，不会重定向到此 `WebView` 目录；原生 Data/State 仍使用上述产品根。

便携模式仅支持 Windows/Linux：使用 `--portable`，或在实际可执行文件旁手动创建内容严格为 `{"version":1}` 的 `portable.json`（允许 JSON 空白，不允许额外/重复字段或其它版本）。已存在但无效的 marker 会报错，不回退安装模式；显式参数不会创建 marker。便携根固定为可执行文件目录内的 `Data`，持久内容直接放在此根内，其下使用 `State`、`Cache`、`WebView`、按需 `Logs`，与启动时的工作目录无关。Linux AppImage 使用有效绝对 `APPIMAGE` 指向的外层包目录作为锚点，marker 也放在外层包旁，不能放在临时只读挂载内。同一规范数据根共用单实例，不同数据根不会互相转发文件。目录不可写时启动失败，不回落到用户安装数据。macOS 遇到参数或有效 marker 会明确拒绝，不写入 .app 内部，以免破坏签名。

便携版仍执行签名策略检查、可信时间、序号防回退和原生能力门禁，并提供官方下载提示；不调用安装型 Updater，不支持自动便携更新。更新时退出应用，手动下载并替换程序，保留整个 Data 目录；不要把安装包当作便携自动更新载荷。

卸载默认保留用户数据。NSIS 仅在用户明确勾选删除数据且不是更新卸载时，删除当前产品的 `%LOCALAPPDATA%\Madis\Peek3D`；不删除用户数据的 Madis 父目录、其它产品或旧 identifier 数据。MSI 不提供自动删除用户数据选项；需要清理时先退出程序、备份，再由用户仅删除上述当前产品根目录。macOS 系统 WebKit 数据也不会被本产品卸载模板自动删除。运行时不识别旧 ID、不自动搬迁；清理 Cache 不会清除 State。

安装、升级、卸载及便携替换受目标系统权限、运行库和签名机制影响。请先备份并在目标环境确认行为；目录契约不代表所有平台组合均获得安装、签名或自动更新保证。

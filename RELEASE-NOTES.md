首个完整依赖分发的 Windows x64 公开测试版。

**想让 Codex 帮你安装？** 将 [本仓库链接](https://github.com/starryxxx5233-netizen/starry-skin-manager-releases) 发给能操作目标电脑的 Codex，并说：“按照 README 的 Codex 安装说明，帮我安装并验证运行。” [查看可直接复制的完整指令](https://github.com/starryxxx5233-netizen/starry-skin-manager-releases#install-with-codex)。

## 下载与使用

- **Setup.exe**：安装程序。
- **Windows-x64.zip**：完整文件夹版，全部解压后运行 `Codex Skin.exe`。
- **SHA256SUMS.txt**：安装程序与 ZIP 的 SHA-256 校验值。

内含兼容皮肤引擎 **5.4.17**、**Node.js 24.16.0** 和 **12 款内置主题**。使用者需要事先安装 Codex 桌面端。GitHub 自动生成的 Source code 压缩包不是程序。

## 界面预览

![Starry 皮肤管理器](https://raw.githubusercontent.com/starryxxx5233-netizen/starry-skin-manager-releases/main/docs/images/starry-manager.png)

截图由项目所有者提供，保持原样；“波奇酱02”为自定义主题，不包含在默认主题包中。

## 功能

- 简洁首页、主题搜索与分页。
- 主题卡片支持跨页拖拽，松手即保存。
- 响应式窗口布局，记住尺寸、位置及最大化状态。
- 保留打开、暂停、恢复、恢复原生、诊断及常驻设置入口。
- 安装时不会自动启用皮肤或常驻。

## 验证范围

74 项自动化测试、7 项实际打包程序检查通过，包括独立配置下的包内引擎/Node 加载、12 款主题、跨页拖拽、重启恢复、小窗口布局和真实只读诊断。

尚未完成另一台干净 Windows 电脑的安装/卸载，以及真实 Codex 应用、暂停、恢复、恢复原生的完整流程。Microsoft Store/MSIX 全路径也未完成验证，因此本版标记为 **Pre-release**。安装程序尚无发布者数字签名。

查看 [使用说明](https://github.com/starryxxx5233-netizen/starry-skin-manager-releases#readme) 与 [完整验证记录](https://github.com/starryxxx5233-netizen/starry-skin-manager-releases/blob/main/VALIDATION.md)。

基于 [HeiGe Codex Skin Studio](https://github.com/HeiGeAi/heige-codex-skin-studio)，保留上游许可及第三方素材声明。非官方工具。

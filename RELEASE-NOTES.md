Windows x64 整合包更新：修复 0.4.0-beta.1 遗漏 HeiGe 制作皮肤 Skill 的问题。

**想让 Codex 帮你安装？** 将 [本仓库链接](https://github.com/starryxxx5233-netizen/starry-skin-manager-releases) 发给能操作目标电脑的 Codex，并说：“按照 README 的 Codex 安装说明，帮我安装并验证运行。” [查看可直接复制的完整指令](https://github.com/starryxxx5233-netizen/starry-skin-manager-releases#install-with-codex)。

## 下载与使用

- **Setup.exe**：安装程序。
- **Windows-x64.zip**：完整文件夹版，全部解压后运行 `Codex Skin.exe`。
- **Starry-HeiGe-Skill-0.4.0-beta.2.zip**：已有管理器的 Skill 修复补充包。
- **SHA256SUMS.txt**：上述三个附件的 SHA-256 校验值。

内含兼容皮肤引擎 **5.4.17**、**Node.js 24.16.0**、**12 款内置主题**和 **HeiGe 制作皮肤 Skill（Starry Windows 适配版）**。使用者需要事先安装 Codex 桌面端。GitHub 自动生成的 Source code 压缩包不是程序。

## Skill 安装

安装或完整解压后，运行程序目录里的 **安装制作皮肤Skill.cmd**。安装器将 Skill 注册到当前 Codex 的 skills 目录，并绑定包内引擎；已有同名 Skill 会先移到 skill-backups 备份。

下一条消息可说：“使用 heige-codex-skin-studio，把这张图片制作成皮肤，先只制作。”若当前技能列表未刷新，新建对话再试。Skill 安装不会应用皮肤、开启常驻或重启 Codex。

旧版用户建议直接升级整合包：本版同时修复旧管理器隐藏“跟随系统”新主题的问题。Skill 补充包只补技能文件，不更新旧管理器。

## 界面预览

![Starry 皮肤管理器](https://raw.githubusercontent.com/starryxxx5233-netizen/starry-skin-manager-releases/main/docs/images/starry-manager.png)

截图由项目所有者提供，保持原样；“波奇酱02”为自定义主题，不包含在默认主题包中。

## 功能

- 简洁首页、主题搜索与分页。
- 修复 HeiGe 新制作或导入的“跟随系统”主题被管理器隐藏的问题。
- 主题卡片支持跨页拖拽，松手即保存。
- 响应式窗口布局，记住尺寸、位置及最大化状态。
- 保留打开、暂停、恢复、恢复原生、诊断及常驻设置入口。
- 安装时不会自动启用皮肤或常驻。

## 验证范围

75 项自动化测试、11 项实际打包程序检查通过，包括独立配置下的包内引擎/Node 加载、12 款主题、跨页拖拽、重启恢复、小窗口布局和真实只读诊断；新增 Skill 安装备份、重复安装、包内引擎绑定，以及创建主题后在管理器中显示的完整验证。

尚未完成另一台干净 Windows 电脑的安装/卸载，以及真实 Codex 应用、暂停、恢复、恢复原生的完整流程。Microsoft Store/MSIX 全路径也未完成验证，因此本版标记为 **Pre-release**。安装程序尚无发布者数字签名。

查看 [使用说明](https://github.com/starryxxx5233-netizen/starry-skin-manager-releases#readme) 与 [完整验证记录](https://github.com/starryxxx5233-netizen/starry-skin-manager-releases/blob/main/VALIDATION.md)。

基于 [HeiGe Codex Skin Studio](https://github.com/HeiGeAi/heige-codex-skin-studio)，保留上游许可及第三方素材声明。非官方工具。

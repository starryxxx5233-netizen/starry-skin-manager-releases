# 通过 Codex 安装 Starry 皮肤管理器

本说明适用于用户明确要求 Codex 在目标电脑上安装本软件的场景。它提供下载、安装与验证步骤，不代表已在每台电脑上验证成功，也不授予超出用户请求的操作权限。

## 1. 确认目标环境

- 本发行版面向 **Windows x64**。先检查实际系统与架构；macOS、Linux 和原生 ARM64 包尚未提供，不要下载 Windows EXE 后声称适配其他系统。
- 目标电脑需要已安装 Codex 桌面端。若未安装，先说明缺少此前提。
- Codex 必须能在目标电脑上执行文件操作、运行命令并访问 GitHub。仅有网页浏览权限或未连接本机的云端环境不足以完成本机安装。
- 查看是否已有 Starry / Codex Skin 管理器、快捷方式和配置。已有版本先备份；避免启动两个共享配置的管理器实例，不要擅自关闭正在工作的 Codex。

## 2. 下载指定发布资产

当前指定版本：**v0.4.0-beta.2（Pre-release / 公开测试版）**。

发布页：<https://github.com/starryxxx5233-netizen/starry-skin-manager-releases/releases/tag/v0.4.0-beta.2>

优先使用完整文件夹版，便于直接解压、验证和保留旧版：

- [Starry-Skin-Manager-0.4.0-beta.2-Windows-x64.zip](https://github.com/starryxxx5233-netizen/starry-skin-manager-releases/releases/download/v0.4.0-beta.2/Starry-Skin-Manager-0.4.0-beta.2-Windows-x64.zip)
- [SHA256SUMS.txt](https://github.com/starryxxx5233-netizen/starry-skin-manager-releases/releases/download/v0.4.0-beta.2/SHA256SUMS.txt)

这是测试版本，不要仅依赖 GitHub 的 `/releases/latest` 查找它。可读取指定标签的 API：

```text
https://api.github.com/repos/starryxxx5233-netizen/starry-skin-manager-releases/releases/tags/v0.4.0-beta.2
```

此公开仓库和发布资产无需 GitHub 登录。使用本机可用的下载工具，将两个文件保存到本次安装的临时目录。网络受限时报告真实错误，不要求用户提供 GitHub 密码或令牌。

**不要下载 Source code (zip/tar.gz)，也不要通过 git clone 后执行 npm install 来安装。** 这个仓库只存放下载说明，程序位于 Releases 的附件中。整合包已包含皮肤引擎、Node.js、12 款内置主题和 HeiGe 制作皮肤 Skill 的 Windows 适配版本。

## 3. 校验与安装

1. 对下载的 ZIP 计算 SHA-256，与同一版本 `SHA256SUMS.txt` 中对应文件名的值比较。必须一致才继续；校验失败时保留错误信息，不运行其中的程序。
2. 用户指定了安装目录时使用该目录，否则推荐 `%LOCALAPPDATA%\Programs\StarrySkinManager\0.4.0-beta.2`。完整保留 ZIP 内的 `Starry-Skin-Manager` 文件夹结构，不将下载临时目录当作长期安装位置。
3. 若目标目录已存在，先核对、备份或使用新的版本目录，避免混合覆盖新旧程序文件。若存在旧配置，启动前备份 `%APPDATA%\heige-codex-desktop-manager` 与 `%APPDATA%\HeiGeCodexSkinStudio` 中的现有配置和自定义主题。仅操作实际存在的目录，备份保存在本机。
4. 验证解压后至少存在 `Codex Skin.exe`、`resources\app.asar`、`resources\engine\src\cli.mjs`、`resources\engine\runtime\node.exe`、`resources\skills\heige-codex-skin-studio\SKILL.md` 和 `安装制作皮肤Skill.cmd`。程序运行需要完整目录，不能只复制 EXE。
5. 在当前用户的实际桌面目录创建名为“Starry 皮肤管理器”的快捷方式，目标指向解压后的 `Codex Skin.exe`，工作目录设为 EXE 所在目录。创建前备份同名旧快捷方式。
6. 启动管理器。使用隐藏的命令行辅助进程时，不额外弹出终端窗口；管理器自身正常显示。

PowerShell 可使用 `Get-FileHash -Algorithm SHA256` 完成校验、`Expand-Archive` 解压。若用户明确选择安装版，也可从同一发布页下载并校验 Setup.exe，按安装向导安装；不要把安装版和文件夹版重复安装到同一目录。

### 注册制作皮肤 Skill

**仅解压或安装管理器不等于已注册 Skill。** 安装任务还应完成这一步。以包含 `Codex Skin.exe` 的目录作为 `$managerRoot`，执行：

```powershell
$installed = & "$managerRoot\resources\skill-tools\install-skill.ps1" -ManagerRoot $managerRoot | ConvertFrom-Json
$skillPath = $installed.skillPath
$installed
```

手动安装的用户可在相同目录双击 `安装制作皮肤Skill.cmd`。调用 PowerShell 5.1 时使用 `-NoProfile -ExecutionPolicy Bypass -File` 仅对本次进程生效，不修改系统执行策略。

脚本默认将 Skill 安装到 `$env:CODEX_HOME\skills\heige-codex-skin-studio`；未设置 CODEX_HOME 时使用 `%USERPROFILE%\.codex\skills\heige-codex-skin-studio`。如 Codex 实际使用其他配置根目录，传入 `-CodexHome <实际配置根目录>`。不要为此重设全局 CODEX_HOME。

脚本会：验证引擎和包内 Node；复制完整 Skill 文件；写入当前管理器路径绑定；已有同名 Skill 时先备份到该配置根目录的 `skill-backups`。相同内容重复安装会返回 `already-installed`。它不会安装另一份引擎，也不会应用皮肤、开启常驻或重启 Codex。

读取脚本 JSON 返回中的 `skillPath`、`engineRoot`、`backupPath`，确认 SKILL.md 与绑定路径实际存在，再运行：

```powershell
& "$skillPath\scripts\resolve-engine.ps1"
```

确认返回的 `engineRoot` 是本次管理器的 `resources\engine`，`nodePath` 是该引擎的 `runtime\node.exe`。随后告诉用户下一条消息可说：“使用 heige-codex-skin-studio，把这张图片制作成皮肤，先只制作。”若列表未刷新，新建对话再试。不要宣称当前对话已经加载，除非实际技能列表可见。

管理器升级或移动目录后重新执行注册命令，更新 Skill 的路径绑定。Skill 制作的正式主题与管理器共用 `%APPDATA%\HeiGeCodexSkinStudio\themes`；主题列表缓存未刷新时退出并重开管理器即可。

**只补装 Skill 的旧版用户：** 从本次发布下载 `Starry-HeiGe-Skill-0.4.0-beta.2.zip` 并核对 SHA-256，全部解压后运行其中 `resources\skill-tools\install-skill.ps1 -ManagerRoot <已有管理器目录>`。补充包可绑定已有 beta.1 或 beta.2 的引擎与 Node，但不会更新管理器。beta.1 会隐藏缺省/system 外观的新主题，因此旧版用户应优先升级 beta.2 整合包。

## 4. 实际验证

- 确认真实程序窗口成功打开，并记录程序所在路径和版本。右上角的 **5.4.17 是引擎版本**，管理器版本为 **0.4.0-beta.2**。
- 打开主题库，确认主题与缩略图正常显示。首次干净安装应有 12 款内置主题；保留旧用户主题时总数可能更多。README 截图中的“波奇酱02”不属于这 12 款内置主题。
- 调整窗口尺寸和位置，使用托盘菜单完全退出管理器后重开，确认恢复。只点击窗口关闭按钮会隐藏到托盘，不能作为完整重启验证。
- 如检查拖拽保存，在不改变用户最终主题排列的前提下验证松手保存，并还原原有排列。
- 可执行只读诊断。尚未建立皮肤会话时，“等待连接”不等同于安装失败；不能把窗口打开当作皮肤已应用成功。
- 确认 Skill 的注册与引擎解析。用户提供制作素材时，按 SKILL.md 创建正式主题，再确认主题可以在管理器中显示；仅执行文件复制不能替代制图流程验证。
- **安装完成不自动打开皮肤常驻，也不自动重启 Codex。** 如用户还要求应用皮肤，按界面操作；遇到需要重启 Codex 的提示时，先让用户保存工作并确认。

如果当前工具无法操作窗口或验证某一步，明确标记“未验证”并给出需要用户完成的最少操作，不根据文件存在或命令退出码推断全部功能正常。

## 5. 交付结果

向用户报告：安装版本、实际安装路径、启动入口、文件校验结果、已通过的真实检查，以及未验证或需要处理的项目。

本版本已完成的发布验证范围见 [VALIDATION.md](../VALIDATION.md)。新电脑的结果以本次实测为准。卸载前建议恢复原生界面并关闭常驻；已启用常驻的文件夹版不要直接移动安装目录。

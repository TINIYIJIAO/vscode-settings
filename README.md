# VSCode 编辑器全局设置

一套适合多语言开发的 VSCode 用户级配置，开箱即用。

## 配置亮点

| 模块 | 说明 |
|------|------|
| 字体 | Maple Mono NF CN 18px，行高 32，中英文混排优化 |
| 连字 | 启用，长时间阅读舒适 |
| 光标 | 平滑动画闪烁，细线样式，2px 宽 |
| 括号 | 彩色染色 + 当前对高亮 + `matchBrackets: always` |
| 缩进 | 缩进引导线替代括号竖线，高亮当前层级 |
| 编辑器 | sticky scroll、语义高亮、选区高亮、linked editing |
| 格式化 | 保存时自动格式化 + fixAll |
| 文件 | 自动保存（1s 延迟）、去尾空格、末尾空行 |
| 终端 | Maple Mono 18px，平滑滚动，10000 行回滚 |
| 主题 | One Dark Pro Darker + Material Icon Theme |

## 快速开始

### 1. 安装字体

```bash
# Maple Mono NF CN — 中英文混排等宽字体
winget install MapleMono

# JetBrains Mono — 备选回退
winget install JetBrains.Mono
```

macOS 用户：

```bash
brew install --cask font-maple-mono
brew install --cask font-jetbrains-mono
```

### 2. 安装插件

打开 VSCode → `Ctrl + Shift + X`，搜索安装以下插件：

| 插件 | 作用 |
|------|------|
| **One Dark Pro** | 主题配色（Dark+ Darker 变体） |
| **Material Icon Theme** | 文件图标主题 |
| **Error Lens** | 行内显示错误/警告，不用鼠标悬停 |
| **Better Comments** | 注释高亮（TODO / FIXME / NOTE 等） |
| **Bracket Pair Color DLW** | 括号对彩色染色增强 |

或者一键安装：

```bash
code --install-extension zhuangtongfa.material-theme
code --install-extension PKief.material-icon-theme
code --install-extension usernamehw.errorlens
code --install-extension aaron-bond.better-comments
code --install-extension BracketPairColorDLW.bracket-pair-color-dlw
```

### 3. 应用配置

**方法 A：复制粘贴（推荐）**

1. 克隆仓库：`git clone https://github.com/TINIYIJIAO/vscode-settings.git`
2. 打开 VSCode → `Ctrl + Shift + P`
3. 输入 `Preferences: Open User Settings (JSON)`
4. 把 `settings.json` 内容粘贴进去，保存
5. `Ctrl + Shift + P` → `Reload Window`

**方法 B：符号链接（适合需要持续 git pull 更新）**

Windows (PowerShell 管理员)：

```powershell
# 备份原有设置
Move-Item $env:APPDATA\Code\User\settings.json $env:APPDATA\Code\User\settings.json.bak

# 创建符号链接
New-Item -ItemType SymbolicLink `
  -Path "$env:APPDATA\Code\User\settings.json" `
  -Target "G:\vscode-settings\settings.json"
```

Linux / macOS：

```bash
ln -sf /path/to/vscode-settings/settings.json ~/.config/Code/User/settings.json
```

## 新机器一键部署

```bash
# 1. 字体
winget install MapleMono JetBrains.Mono

# 2. 配置
git clone https://github.com/TINIYIJIAO/vscode-settings.git

# 3. 插件
code --install-extension zhuangtongfa.material-theme
code --install-extension PKief.material-icon-theme
code --install-extension usernamehw.errorlens
code --install-extension aaron-bond.better-comments
code --install-extension BracketPairColorDLW.bracket-pair-color-dlw

# 4. 把 settings.json 粘贴到 VSCode 用户设置 → Reload Window
```

## 自定义

此配置是通用基础版。每个项目的特殊设置放在项目根目录 `.vscode/settings.json` 中，会自动叠加生效。

例如 FPGA 项目可以添加：

```jsonc
{
  "[verilog]": {
    "editor.tabSize": 4
  },
  "files.exclude": {
    "**/work": true,
    "**/*.vcd": true
  }
}
```

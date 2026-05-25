# VSCode 编辑器全局设置

一套适合多语言开发的 VSCode 用户级配置，开箱即用。

## 配置亮点

| 模块 | 说明 |
|------|------|
| 字体 | Cascadia Code → JetBrains Mono → Fira Code 回退链，16px，行高 1.6 |
| 连字 | 启用 calt + 全套 stylistics sets，零加斜线区分 O/0 |
| 光标 | 平滑动画闪烁，2px 线宽 |
| 标尺 | 80 / 100 / 120 三线参考 |
| 缩进 | 默认 4 空格，JSON/YAML/前端用 2 空格 |
| 终端 | 等宽 14px，行高 1.3，光标闪烁 |
| 文件排除 | 隐藏 `__pycache__`、`node_modules`、`.DS_Store` 等通用噪音 |

## 快速开始

### 1. 安装字体（二选一，推荐都装）

```bash
# Cascadia Code — 微软出品，Windows Terminal 自带
winget install Microsoft.CascadiaCode

# JetBrains Mono — 备选回退
winget install JetBrains.Mono
```

macOS 用户：

```bash
brew install --cask font-cascadia-code
brew install --cask font-jetbrains-mono
```

### 2. 应用配置

**方法 A：复制粘贴（推荐，简单直接）**

1. 克隆仓库：`git clone <your-remote-url>`
2. 打开 VSCode → `Ctrl + Shift + P`
3. 输入 `Preferences: Open User Settings (JSON)`
4. 把 `settings.json` 内容粘贴进去，保存

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

## 新机器部署

```bash
git clone <your-remote-url>
# 然后按上面「应用配置」的步骤操作
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

# Windows 部署

## 前提条件

- Python 3.8 或更高版本
- 已添加到系统 PATH

## 部署步骤

### 1. 安装依赖

```powershell
pip install -r requirements.txt
```

### 2. 配置 `config.json`

编辑 `config.json`，填入 Bot Token 和管理员用户名。

```json
{
  "bot_token": "YOUR_BOT_TOKEN_HERE",
  "proxy": "",
  "admin_username": "YOUR_USERNAME"
}
```

### 3. 启动机器人

双击 `start.bat`，或在命令行运行：

```powershell
python bot.py
```

### 4. 后台运行（可选）

使用 `pythonw.exe` 在后台运行（不显示控制台窗口）：

```powershell
pythonw bot.py
```

### 5. 开机自启

1. 创建一个 `bot.vbs` 快捷方式文件：
```vbscript
Set WinScriptHost = CreateObject("WScript.Shell")
WinScriptHost.Run Chr(34) & "C:\path\to\telegram-bridge\start.bat" & Chr(34), 0
Set WinScriptHost = Nothing
```
2. 将 `bot.vbs` 放入 `shell:startup` 文件夹

## 代理配置

如需要代理，在 `config.json` 中设置：

```json
{
  "proxy": "http://127.0.0.1:7890"
}
```

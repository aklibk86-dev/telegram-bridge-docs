# 快速开始

## 前提条件

- Python 3.8 或更高版本
- 一个 Telegram 机器人 Token（通过 [@BotFather](https://t.me/BotFather) 创建）

## 第一步：获取 Bot Token

1. 在 Telegram 中打开 [@BotFather](https://t.me/BotFather)
2. 发送 `/newbot` 并按照提示操作
3. 创建成功后，保存获得的 API Token

## 第二步：下载项目

```bash
git clone https://github.com/anomalyco/telegram-bridge.git
cd telegram-bridge
```

## 第三步：修改配置

编辑 `config.json`，填写 Bot Token 和你的管理员用户名：

```json
{
  "bot_token": "YOUR_BOT_TOKEN_HERE",
  "proxy": "",
  "admin_username": "YOUR_TELEGRAM_USERNAME",
  "auto_reply": "我是一个 Telegram 桥接机器人，你的消息已转发给管理员，请耐心等待回复。",
  "auto_reply_delete_time": 0,
  "welcome_message": "欢迎使用！我是 Telegram 桥接机器人。"
}
```

> `admin_username` **不要**加 `@` 前缀。

## 第四步：安装依赖

```bash
pip install -r requirements.txt
```

## 第五步：启动机器人

```bash
python bot.py
```

## 第六步：注册管理员

1. 在 Telegram 中找到你的机器人，发送 `/start`
2. 机器人将提示你输入管理员密码
3. 输入你在 `config.json` 中设置的 `admin_username`
4. 完成注册，现在你可以作为管理员收发消息了

## 验证运行状态

- 用另一个 Telegram 账号向机器人发送消息
- 管理员账号应收到转发的消息
- 管理员回复后，用户应收到回复

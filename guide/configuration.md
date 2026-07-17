# 配置说明

`config.json` 是机器人的配置文件，所有字段说明如下：

## 基础配置

| 字段 | 类型 | 必填 | 说明 |
|------|------|------|------|
| `bot_token` | string | ✅ | BotFather 获取的 API Token |
| `proxy` | string | ❌ | HTTP 代理地址，留空表示直连（国内服务器可设为 `http://127.0.0.1:7890`） |
| `admin_username` | string | ✅ | 管理员的 Telegram 用户名（**不要**加 `@`） |

## 消息配置

| 字段 | 类型 | 说明 |
|------|------|------|
| `auto_reply` | string | 默认自动回复文本，用户发送消息后自动回复此内容 |
| `auto_reply_delete_time` | integer | 自动回复消息的自动删除时间（秒），`0` 表示不删除 |
| `welcome_message` | string | 用户首次 `/start` 时显示的欢迎消息 |

## 关键字配置

`keywords` 是一个对象，键为触发词（关键字），值为回复配置：

```json
{
  "keywords": {
    "帮助": {
      "reply": "这是帮助信息...",
      "buttons": [{"text": "官网", "url": "https://example.com"}]
    },
    "联系": {
      "reply": "请联系管理员 @admin",
      "buttons": []
    }
  }
}
```

每个关键字可独立配置：
- `reply` - 匹配时的回复内容
- `buttons` - 附带的内联按钮（可选）

## 按钮配置

| 字段 | 类型 | 说明 |
|------|------|------|
| `inline_buttons` | array | `/menu` 命令显示的按钮 |
| `auto_reply_buttons` | array | 自动回复消息附带的按钮 |
| `welcome_buttons` | array | 欢迎消息附带的按钮 |
| `broadcast_buttons` | array | 广播消息附带的按钮 |

按钮格式：
```json
[
  {"text": "按钮名称", "url": "https://example.com"}
]
```

## 回复键盘

`reply_keyboard` 为管理员自定义底部分行键盘：

```json
{
  "reply_keyboard": [
    ["帮助", "状态"],
    ["联系方式"]
  ]
}
```

每行一个数组，按钮按顺序排列。

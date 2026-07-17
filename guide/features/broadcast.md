# 广播消息

管理员可以通过 `/broadcast` 命令向所有注册用户群发消息。

## 使用方式

### 命令行模式

```
/broadcast 大家好，系统将于今晚 23:00-23:30 进行维护升级。
```

### 带按钮的广播

发送 `/broadcast` 后会进入引导流程，机器人会依次询问：
1. 广播内容（文字或媒体）
2. 是否附带内联按钮
3. 按钮的文本和 URL
4. 确认发送

## 注意事项

- 广播只会发送给**已注册**的用户（使用过 `/start` 的用户）
- 广播消息可以附带 `broadcast_buttons` 配置的按钮
- 发送前请确认内容，避免误操作
- 大量用户时发送可能需要一些时间（受 Telegram API 频率限制）

## 配置默认广播按钮

在 `config.json` 的 `broadcast_buttons` 中设置：

```json
{
  "broadcast_buttons": [
    {"text": "查看详情", "url": "https://example.com"}
  ]
}
```

或在 `/settings` → 按钮管理 → 广播作用域中配置。

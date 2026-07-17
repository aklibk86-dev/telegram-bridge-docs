# 内联按钮

TeleBridge 支持在多个作用域配置 URL 内联按钮，增强消息交互性。

## 按钮作用域

| 作用域 | 配置字段 | 显示位置 |
|--------|----------|----------|
| 菜单 | `inline_buttons` | `/menu` 命令回复中 |
| 自动回复 | `auto_reply_buttons` | 默认自动回复消息中 |
| 欢迎 | `welcome_buttons` | 用户 `/start` 的欢迎消息中 |
| 广播 | `broadcast_buttons` | 广播消息中 |
| 关键字 | `keywords[key].buttons` | 该关键字触发后的回复中 |

## 按钮格式

```json
{
  "text": "显示文本",
  "url": "https://example.com"
}
```

## 通过 `/settings` 管理按钮

1. 发送 `/settings`
2. 选择「按钮管理」
3. 选择需要配置的作用域（菜单/自动回复/欢迎/广播/关键字）
4. 可进行：查看 / 添加 / 删除 / 清空操作
5. 添加时依次输入按钮文本和 URL

## 配置示例

```json
{
  "inline_buttons": [
    {"text": "官方网站", "url": "https://example.com"},
    {"text": "联系客服", "url": "https://t.me/support"}
  ],
  "auto_reply_buttons": [
    {"text": "常见问题", "url": "https://example.com/faq"}
  ],
  "welcome_buttons": [
    {"text": "快速开始", "url": "https://example.com/start"},
    {"text": "使用指南", "url": "https://example.com/guide"}
  ]
}
```

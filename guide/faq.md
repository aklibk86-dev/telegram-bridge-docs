# 常见问题

## 机器人没有响应 / 网络超时

如果机器人启动后没有响应，通常是网络问题：

**国内服务器：**
- 确保 `config.json` 中配置了代理：`"proxy": "http://127.0.0.1:7890"`
- 检查代理是否正常运行

**海外服务器：**
- 确保 `proxy` 字段为空：`"proxy": ""`
- 检查服务器能否访问 api.telegram.org

## 如何注册为管理员？

向机器人发送 `/start`，按照提示输入你在 `config.json` 中设置的 `admin_username`（不带 `@`）。

## 修改配置后需要重启吗？

通过 `/settings` 面板修改的配置**实时生效**，无需重启。

直接编辑 `config.json` 文件后，需要重启机器人才能生效。

## 如何查看自己的用户名？

在 Telegram 中：
1. 打开 设置 → 用户名
2. 或在任意聊天中发送 `/id` 给 [@userinfobot](https://t.me/userinfobot)

## 如何添加更多管理员？

目前设计为单管理员模式。如需多管理员，可以通过修改 `is_admin` 函数的逻辑来实现。

## 数据文件在哪？

- **用户数据**：`data/users.json`
- **日志文件**：`data/bot.log`
- **配置文件**：`config.json`（项目根目录）

## Docker 部署修改配置后无法生效？

Docker 部署中 `config.json` 是只读挂载的，修改后需要：

```bash
docker compose restart
```

## 如何更新机器人？

```bash
git pull
# 如果依赖有变化：
pip install -r requirements.txt
# 重启机器人
```

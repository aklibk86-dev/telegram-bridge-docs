# Docker 部署

使用 Docker 可以快速部署 TeleBridge，无需手动配置 Python 环境。

## 前提条件

- 已安装 Docker 和 Docker Compose

## 部署步骤

### 1. 配置 `config.json`

在项目根目录下编辑 `config.json`，填入 Bot Token 和管理员用户名。

### 2. 启动服务

```bash
docker compose up -d --build
```

### 3. 查看日志

```bash
docker compose logs -f
```

### 4. 重启服务

修改 `config.json` 后需要重启容器才能生效：

```bash
docker compose restart
```

## 目录结构

```
telegram-bridge/
├── docker-compose.yml
├── Dockerfile
├── config.json        # 配置文件（容器内只读）
└── data/              # 持久化数据（users.json, bot.log）
```

## 数据持久化

- `./data` 目录挂载到容器的 `/app/data`
- 用户数据和日志文件保存在此处
- 删除容器后数据不会丢失

## 自定义环境变量

可在 `docker-compose.yml` 中设置 `DATA_DIR` 环境变量自定义数据目录：

```yaml
environment:
  - DATA_DIR=/app/data
```

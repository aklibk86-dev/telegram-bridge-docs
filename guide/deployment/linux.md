# Linux 部署

## 方法一：一键部署

项目提供了自动化部署脚本：

```bash
sudo bash deploy.sh
```

脚本会自动：
1. 检测 Python 版本（需要 3.8+）
2. 如需安装 Python，可选择自动编译最新版本
3. 复制文件到 `/opt/telegram-bot`
4. 创建虚拟环境并安装依赖
5. 安装 `telegram-bot.service` 为 systemd 服务
6. 启动并启用服务

## 方法二：手动部署

### 1. 准备环境

```bash
# 复制项目文件
cp -r telegram-bridge /opt/telegram-bot
cd /opt/telegram-bot

# 创建虚拟环境
python3 -m venv venv
source venv/bin/activate

# 安装依赖
pip install -r requirements.txt
```

### 2. 配置 systemd 服务

```bash
sudo cp telegram-bot.service /etc/systemd/system/
sudo systemctl daemon-reload
sudo systemctl enable telegram-bot
sudo systemctl start telegram-bot
```

### 3. 查看状态

```bash
sudo systemctl status telegram-bot
sudo journalctl -u telegram-bot -f
```

## 方法三：手动运行

```bash
bash start.sh
```

## 代理配置

如服务器位于中国大陆，需要在 `config.json` 中配置代理：

```json
{
  "proxy": "http://127.0.0.1:7890"
}
```

海外服务器留空即可。

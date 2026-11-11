# 金龙威 Telegram 客服机器人

本项目的机器人菜单、客户提示、管理员面板、统计信息和操作回复均使用简体中文。

## 功能
- 客户菜单：`/start`、联系客服、工单状态、服务说明。
- 客户留言自动转发给已配置的管理员。
- 管理面板：`/admin`，包含数据统计、待处理工单、客户列表和群发说明。
- 管理员回复：`/reply 客户ID 回复内容`。
- 群发通知：`/broadcast 通知内容`。
- SQLite 保存客户、工单和消息记录。
- 网站状态页 `/` 与健康检查 `/health`。

## 创建机器人
1. 在 Telegram 打开官方 `@BotFather`。
2. 发送 `/newbot` 并按提示创建机器人。
3. 复制机器人 Token，妥善保密，不要提交到 GitHub。

## 获取管理员 Telegram ID
可在 Telegram 中通过 `@userinfobot` 查询自己的数字 ID。将数字 ID 填入 `ADMIN_IDS`。多个管理员 ID 用英文逗号分隔。

## 本地运行
1. 安装 Node.js 20 或更新版本。
2. 复制 `.env.example` 为 `.env`。
3. 填写 `BOT_TOKEN`、`ADMIN_IDS`。
4. 执行 `npm install`，然后执行 `npm start`。

## 部署到 Render
1. 解压 ZIP，将文件上传到新的 GitHub 仓库。
2. Render > New > Web Service，连接该仓库。
3. Runtime 选择 Node。
4. Build Command：`npm install`
5. Start Command：`npm start`
6. 添加环境变量：
   - `BOT_TOKEN`：BotFather 提供的 Token
   - `ADMIN_IDS`：管理员数字 ID
   - `DATABASE_PATH`：`./data/jinlongwei.sqlite`
7. 部署完成后打开 Render 提供的网址检查状态，再到 Telegram 向机器人发送 `/start`。

## 重要说明
- Render 免费实例可能休眠，机器人不一定能全天候即时响应。
- SQLite 位于本地文件系统；免费实例重启或重新部署时数据可能丢失。正式运营建议使用 PostgreSQL 或持久化磁盘。
- 请勿公开 Token、客户隐私或提交 `.env` 文件。
- 群发仅用于向主动启动机器人且合理期待接收通知的用户发送相关信息，遵守 Telegram 规则。
- 当前版本支持文本客服。图片、语音、文件、客服网页工作台和多客服分配尚未实现。

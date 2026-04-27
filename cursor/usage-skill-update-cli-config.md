# Cursor Skill Usage: `update-cli-config`

## 一句话怎么用

当你要调整 Cursor CLI 行为时说：  
**“请用 `update-cli-config` 修改 `~/.cursor/cli-config.json` 的 XXX 设置。”**

---

## 使用前建议给的输入

- 要修改的配置键（如 `approvalMode`、`editor.vimMode`）
- 目标值（如 `unrestricted`、`true`）
- 是否仅当前项目覆盖（`.cursor/cli.json`）或全局生效（`~/.cursor/cli-config.json`）

---

## 推荐使用步骤

1. 先让 Cursor 读取当前 CLI 配置
2. 仅修改你指定的字段
3. 要求它回报“改前/改后”
4. 重启 CLI 会话验证生效

---

## 可直接复用的提问模板

- `请用 update-cli-config 把 approvalMode 改成 unrestricted。`
- `请开启 vim 模式：editor.vimMode=true。`
- `请把 display.showLineNumbers 设为 true。`
- `只改这个字段，其他配置不要动。`

---

## 成功判断标准

- 目标字段值正确更新
- 非目标字段保持不变
- 配置 JSON 语法有效
- 重启 CLI 后行为符合预期

---

## 常见失败点

- 混淆全局配置与项目覆盖配置
- 修改了内部缓存字段（不该手改）
- 一次改动过多，问题难定位
- 改完未重启 CLI，误判为未生效


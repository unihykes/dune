# Cursor Skill Usage: `statusline`

## Skill 目的

`statusline` 用于自定义 Cursor CLI 提示符上方状态行。  
你可以把会话信息（模型、上下文使用率、分支等）实时显示出来，便于长会话管理。

---

## 工作机制

- 每次会话更新时，CLI 会执行你配置的命令
- 命令从 stdin 收到一段 JSON payload（会话上下文）
- 命令 stdout 的内容会被渲染成状态行

---

## 基础配置

在 `~/.cursor/cli-config.json` 中配置：

- `statusLine.type`: 固定 `"command"`
- `statusLine.command`: 脚本路径或内联命令
- 可选：`padding`、`updateIntervalMs`、`timeoutMs`

---

## 常见展示字段

- 模型名：`model.display_name`
- 上下文使用率：`context_window.used_percentage`
- 当前目录：`workspace.current_dir`
- 会话名/工作树信息（按需显示）

---

## 实战建议

- 先做最小版本：模型名 + 上下文占用
- 再加一项最有价值信息（如 git 分支）
- 保持单行简洁，避免干扰输入
- 为脚本设置超时，避免卡住渲染

---

## 调试方法

- 用一段 mock JSON 管道给脚本做本地测试
- 检查输出是否包含预期字段与格式
- 注意字段可能缺失或为 null，脚本要兜底

---

## 常见误区

- 把状态行做成复杂仪表盘，影响可读性
- 假设字段永远存在，不做空值处理
- 更新间隔过短导致频繁开销


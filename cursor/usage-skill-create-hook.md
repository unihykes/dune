# Cursor Skill Usage: `create-hook`

## Skill 目的

`create-hook` 用于在 Cursor 中创建自动化钩子（Hooks），让某些事件发生前后自动执行校验、拦截、补充上下文或后续动作。

---

## 先理解 Hook 的价值

你可以把 Hook 当成“智能守门员”或“自动流程节点”：

- 在执行危险命令前二次确认
- 在文件改动后自动格式化/检查
- 在工具调用前后做审计和策略控制

---

## 配置位置

- 项目级：`.cursor/hooks.json`（建议用于团队共享）
- 用户级：`~/.cursor/hooks.json`（个人全局规则）

---

## 关键配置字段

- `version`: 目前常用 `1`
- `hooks`: 事件到 hook 列表的映射
- `command` / `type` / `timeout` / `matcher` / `failClosed`

---

## 常见事件选择

- `beforeShellExecution`: 执行 shell 前拦截
- `afterShellExecution`: 执行后审计输出
- `preToolUse` / `postToolUse`: 工具调用前后治理
- `afterFileEdit`: 编辑后自动处理
- `beforeSubmitPrompt`: Prompt 发出前做安全检查

选择原则：优先用“最窄事件”，减少误触发。

---

## 使用步骤（实战）

1. 明确目标（要拦截什么/自动做什么）
2. 选事件与作用域（项目级或用户级）
3. 写 `hooks.json`
4. 写脚本（command hook）或 prompt hook
5. 先不加复杂 matcher，跑通后再收紧
6. 实际触发事件进行验证

---

## 注意事项

- `matcher` 是 JavaScript 正则，不是 grep/POSIX 正则
- 需要阻断时考虑 `failClosed: true`
- 脚本依赖命令必须真实可用，不能想当然

---

## 常见误区

- 一开始就写复杂 matcher，结果 hook 不触发
- 输出字段与事件不匹配（例如返回不支持的字段）
- 把用户级路径写成项目级相对路径，导致找不到脚本


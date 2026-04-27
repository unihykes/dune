# Cursor Skill Usage: `create-hook`

## 一句话怎么用

你想让 Cursor 在某个事件“自动检查/拦截/补充动作”时，直接说：  
**“请用 create-hook 帮我创建一个 Hook，事件是 XXX，行为是 YYY。”**

---

## 先给这 4 个关键信息

发需求时尽量一次说全：

- **Scope**：项目级还是用户级
- **Trigger**：挂在哪个事件（如 `beforeShellExecution`）
- **Behavior**：允许/拦截/改写/补充上下文
- **Safety**：失败时放行还是阻断（`failClosed`）

---

## 常见“需求 -> 事件”速查

- 拦截危险终端命令 -> `beforeShellExecution`
- 文件改完自动格式化 -> `afterFileEdit`
- 工具调用前做策略校验 -> `preToolUse`
- Prompt 发出前查敏感词 -> `beforeSubmitPrompt`

---

## 推荐使用步骤（照着提）

1. “先给我一个最小可用 Hook，不加复杂 matcher。”
2. “跑通后再收紧 matcher，只匹配目标命令/工具。”
3. “告诉我如何验证触发成功，以及失败时行为。”

---

## 可直接复用的提问模板

- `请用 create-hook 做一个项目级 hook：在 beforeShellExecution 阶段拦截 curl/wget，失败时 failClosed=true。`
- `先给最小版本，确认可触发后再加 matcher。`
- `请把 hooks.json 和脚本都创建好，并告诉我如何手动验证。`

---

## 成功判断标准

- 触发了正确事件（不是“看起来写了”）
- 返回字段符合该事件支持范围
- 错误时行为符合预期（放行或阻断）
- 规则只影响目标场景，不误伤日常操作

---

## 常见失败点

- 一上来就写复杂 matcher，导致不触发
- 事件和目标不匹配（比如应该 before 却配到 after）
- 脚本依赖缺失，实际运行失败
- 相对路径写错，Cursor 找不到 hook 脚本


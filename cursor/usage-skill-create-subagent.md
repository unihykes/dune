# Cursor Skill Usage: `create-subagent`

## 一句话怎么用

当你想把某类任务“交给专用小助手”时说：  
**“请用 `create-subagent` 帮我创建一个子代理，专门处理 XXX。”**

---

## 你需要先给的信息

- 子代理用途（如 code review、debug、数据分析）
- 作用范围（项目级 `.cursor/agents/` 或用户级 `~/.cursor/agents/`）
- 触发时机（什么时候应该委派给它）
- 输出要求（返回格式、优先级、是否要证据）

---

## 推荐使用步骤

1. 先让 Cursor 帮你定义 `name` 与 `description`
2. 要求 `description` 写清“WHEN”（何时触发）
3. 让 Cursor 生成子代理 `.md` 文件
4. 用 1~2 个真实任务测试是否被正确调用
5. 根据命中效果微调描述与提示词

---

## 可直接复用的提问模板

- `请用 create-subagent 创建一个 project subagent，名字叫 code-reviewer。`
- `description 要明确：改完代码后应主动触发（use proactively）。`
- `系统提示里请写清工作流：先看 diff，再按严重度输出问题。`
- `请给我一条测试指令，验证这个子代理能被调用。`

---

## 成功判断标准

- 子代理文件位置正确（项目级或用户级）
- `name` 合法（小写+连字符）且唯一
- `description` 足够具体，能稳定触发委派
- 子代理输出符合你定义的流程和格式

---

## 常见失败点

- 描述太泛（如“helps with code”），导致不触发
- 一个子代理承担太多职责，边界模糊
- 放错目录或 frontmatter 语法错误
- 只创建不测试，实际命中率未知


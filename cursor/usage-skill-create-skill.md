# Cursor Skill Usage: `create-skill`

## Skill 目的

`create-skill` 用于帮助你设计和编写新的自定义 Skill，让 AI 在特定场景下具备稳定、可复用、可团队共享的工作流能力。

---

## 先理解 skill 是什么

Skill 本质是“任务方法论 + 触发条件 + 输出规范”的封装。  
典型用途：

- PR review 标准化
- 提交信息格式化
- 某类数据查询/分析流程固化

---

## 存放位置

- 个人技能：`~/.cursor/skills/skill-name/`
- 项目技能：`.cursor/skills/skill-name/`

不要把自定义技能放进 `~/.cursor/skills-cursor/`，那是 Cursor 内置技能目录。

---

## 必备文件

每个 skill 目录至少有一个 `SKILL.md`，包含：

- frontmatter：`name`、`description`
- 正文：步骤、约束、示例、参考链接

---

## 关键设计原则

- 描述要同时写清 WHAT + WHEN（做什么 + 何时触发）
- 用第三人称写 `description`，提高匹配稳定性
- 主文档尽量简洁，把细节放到引用文件（渐进展开）
- 命名统一、术语一致，减少歧义

---

## 推荐创建流程

1. 需求澄清：目标、触发词、输出格式
2. 设计结构：name/description/章节骨架
3. 编写实现：`SKILL.md` + 可选参考文档
4. 验证迭代：在真实任务里观察命中率与输出质量

---

## 常见误区

- `description` 太泛，导致 skill 不被触发
- 文档过长且重复，消耗上下文但增益有限
- 一个 skill 想覆盖太多任务，边界不清晰


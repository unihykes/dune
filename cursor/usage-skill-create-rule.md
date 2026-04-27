# Cursor Skill Usage: `create-rule`

## Skill 目的

`create-rule` 用于创建 Cursor 持久规则，让 AI 在后续会话中长期遵守你的项目规范、文件约束和团队约定。

---

## 规则存放位置

规则文件放在：`.cursor/rules/`  
文件后缀：`.mdc`

---

## Rule 基本结构

每个规则包含 YAML frontmatter + markdown 正文。frontmatter 常见字段：

- `description`: 规则作用描述
- `globs`: 文件匹配范围（文件级规则）
- `alwaysApply`: 是否全局总是生效

---

## 何时用 alwaysApply

- 项目通用原则（如日志、异常处理、命名约定）
- 与文件类型无关的工作方式约束

## 何时用 globs

- 只针对特定文件类型（如 `**/*.ts`、`backend/**/*.py`）
- 前后端规范不同，需要按目录区分

---

## 推荐写法

- 一条规则只聚焦一个主题
- 给可执行示例（bad/good）而不是抽象口号
- 内容保持精炼，便于长期维护

---

## 实战步骤

1. 先定义目的（要约束什么）
2. 决定作用范围（全局 or 文件匹配）
3. 写 `.mdc` frontmatter
4. 写规则正文与修复示例
5. 在真实任务中观察是否生效并迭代

---

## 常见误区

- globs 写得过宽，导致无关文件也受影响
- 一个规则塞太多主题，后期难维护
- 只有原则没有示例，AI 执行时不稳定


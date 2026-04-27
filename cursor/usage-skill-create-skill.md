# Cursor Skill Usage: `create-skill`

## 一句话怎么用

当你要“把某类工作流程固化成可复用能力”时，直接说：  
**“请用 create-skill 帮我创建一个 skill，名称是 XXX，用于 YYY。”**

---

## 发起时建议一次给全的信息

- Skill 目标：这个技能要解决什么问题
- 存放位置：个人（`~/.cursor/skills/`）还是项目（`.cursor/skills/`）
- 触发场景：用户说什么话时应该启用它
- 输出格式：希望模型按什么模板产出

---

## 推荐使用步骤

1. 先让 Cursor 帮你定 `name` 和 `description`
2. 要求 `description` 写清 WHAT + WHEN
3. 让 Cursor 生成 `SKILL.md` 骨架
4. 补充示例与边界条件
5. 用真实指令测试是否能稳定命中

---

## 可直接复用的提问模板

- `请用 create-skill 创建一个 project skill：name=api-review，用于审查接口兼容性。`
- `description 必须包含触发词，比如“接口变更、API review、向后兼容”。`
- `先给最小可用 SKILL.md，再给可选的 examples.md。`
- `请保证术语统一，避免同义词混用。`

---

## 成功判断标准

- Skill 目录结构正确，含 `SKILL.md`
- `name` 合法（小写+连字符）且语义清晰
- `description` 能让系统在正确场景触发
- 真实任务里能稳定产出预期格式

---

## 常见失败点

- `description` 太抽象，触发率低
- 一个 skill 试图覆盖太多场景
- 文档冗长却缺少可执行模板
- 放错目录（尤其误放到内置 skills 目录）


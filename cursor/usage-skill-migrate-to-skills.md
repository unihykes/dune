# Cursor Skill Usage: `migrate-to-skills`

## 一句话怎么用

当你要把旧的 Rule/Slash Command 迁移到 Skill 时说：  
**“请用 `migrate-to-skills` 把可迁移规则和命令转换到 `.cursor/skills/`。”**

---

## 迁移前你必须知道

- 迁移核心原则：**正文必须逐字符保留，不要改写**
- Rule 仅迁移“Applied intelligently”类型（有 `description`，且无 `globs`、无 `alwaysApply: true`）
- Command 会整体迁移，并补 skill frontmatter

---

## 推荐使用步骤

1. 先让 Cursor 列出“将被迁移的文件清单”
2. 让它按类型分组（rules / commands）
3. 你确认清单后再执行迁移
4. 迁移后让它给“旧路径 -> 新路径”对照表
5. 最后要求提供“可回滚说明”

---

## 可直接复用的提问模板

- `请用 migrate-to-skills 先扫描并列出可迁移文件，不要直接改。`
- `迁移时严格保留 body 原文，不要修正格式或措辞。`
- `执行后请输出每个文件的旧路径和新 skill 路径。`
- `如果我要撤销迁移，请给我一键回退方案。`

---

## 成功判断标准

- 迁移后的 `SKILL.md` frontmatter 正确
- 原正文内容与旧文件完全一致（字符级）
- 旧文件是否删除符合你的决策
- 迁移清单完整、可追溯、可回滚

---

## 常见失败点

- 边迁移边“优化文案”，破坏原意
- 没先出清单，直接批量操作
- 忽略用户级与项目级路径差异
- 迁移后无映射表，后续难审计


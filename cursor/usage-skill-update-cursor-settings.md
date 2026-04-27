# Cursor Skill Usage: `update-cursor-settings`

## 一句话怎么用

当你想“用自然语言改 Cursor 设置”时，直接说：  
**“请用 update-cursor-settings 把 XXX 改成 YYY。”**

---

## 推荐你这样提需求

尽量包含：

- 要改的设置项（或明确意图）
- 目标值（如 `16`、`true`、某主题名）
- 作用范围（全局用户设置或当前工作区）

---

## 常见指令模板

- `请用 update-cursor-settings 把 editor.fontSize 改为 16。`
- `请开启 format on save（editor.formatOnSave=true）。`
- `请把主题切到 Default Dark Modern。`
- `仅改当前项目，不要改全局设置。`

---

## 推荐使用步骤

1. 先让 Cursor 读取现有设置
2. 只改你指定的键值
3. 保留其它配置不动
4. 改完后让它回报变更项
5. 需要时重载窗口验证生效

---

## 成功判断标准

- 目标设置项值正确
- 非目标配置未被误改
- JSON/JSONC 结构未破坏
- 你知道是否需要 reload 才生效

---

## 常见失败点

- 需求模糊（只说“调舒服点”）
- 忘记说明作用范围（全局 vs 工作区）
- 批量改太多设置，难以定位问题
- 改后不验证，误以为没生效


# Cursor Skill Usage: `shell`

## 一句话怎么用

你希望“把一条命令原样执行”时，用 `/shell`：  
**`/shell <你的命令>`**

---

## 这个 skill 的关键特性

- 只在你**显式使用 `/shell`** 时生效
- `/shell` 后面的文本会被当作**字面命令**直接执行
- 不会先帮你改写或优化命令

---

## 正确使用步骤

1. 写 `/shell` 并紧跟具体命令
2. 一次执行一条命令，便于定位结果
3. 看返回的退出码与关键输出
4. 需要继续时再发下一条 `/shell`

---

## 可直接复用的提问模板

- `/shell git status --short --branch`
- `/shell npm test`
- `/shell python scripts/check.py`
- `/shell ls -la`

---

## 成功判断标准

- 命令被原样执行（无改写）
- 返回有明确 exit status
- 关键 stdout/stderr 被反馈
- 你能基于结果继续下一步操作

---

## 常见失败点

- 只写 `/shell` 不跟命令
- 误以为它会自动纠错或重写命令
- 把多步复杂流程塞成一条超长命令
- 忽略退出码，只看部分输出


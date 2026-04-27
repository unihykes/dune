# Cursor Skill Usage: `update-cursor-settings`

## Skill 目的

`update-cursor-settings` 用于修改 Cursor/VSCode 的用户设置（`settings.json`），把“口头偏好”快速落地为编辑器配置。

---

## 适用场景

- 调整字体、主题、tab 宽度、自动保存
- 开关 format on save、word wrap、minimap 等
- 修改终端与工作台偏好

---

## 设置文件位置（Windows）

- 用户设置：`%APPDATA%/Cursor/User/settings.json`
- 作用范围：全局生效（所有项目）

对比：

- 工作区设置：`.vscode/settings.json`（仅当前项目）

---

## 标准操作流程

1. 先读取现有设置
2. 只改用户要求的键值
3. 保留其它已有配置
4. 写回并保证 JSON 语法有效
5. 告知是否需要重载窗口

---

## 常见“需求 -> 设置项”映射

- 调大字体 -> `editor.fontSize`
- 自动保存 -> `files.autoSave`
- 保存即格式化 -> `editor.formatOnSave`
- 更换主题 -> `workbench.colorTheme`
- 隐藏 minimap -> `editor.minimap.enabled`

---

## 注意事项

- `settings.json` 可能包含注释（JSONC），处理时不要破坏结构
- 大改动建议可回退（备份或版本控制）
- 用户设置和工作区设置要区分清楚，避免改错位置

---

## 常见误区

- 不读原文件直接覆盖，导致用户配置丢失
- 把“项目级需求”误改到全局用户设置
- 改完不提醒是否需要 reload，用户误以为未生效


# codex AGENTS.md 说明
参考: https://developers.openai.com/codex/guides/agents-md
```
Give Codex extra instructions and context for your project
```

## 一. 发现机制
```
Codex builds an instruction chain when it starts
```
Codex 在启动时会建立一条指令链

### 何时触发
```
once per run; in the TUI this usually means once per launched session.
```
run 是启动会话这一下,指令链在此时创建一次,之后这个会话里你发多少轮 prompt 都复用同一条链,不会重新发现。

实际影响:会话已经起来之后你去改 `AGENTS.md`,当前会话不会重新加载它——得开个新会话才能让改动生效。

### 读取顺序
```
Discovery follows this precedence order:
```
发现遵循以下优先顺序
- 1.全局层:在 Codex home 目录(~/.codex)读 `AGENTS.override.md`, 若没有(或为空)则读 `AGENTS.md`。
- 2.项目层:从项目根沿目录树一路往下走到当前工作目录,每一级都尝试读取AGENTS.override.md, 若没有则读取 `AGENTS.md`。

### 优先级
按照`发现顺序`将读取的内容向后拼接,越靠近当前目录的AGENTS.md在拼接结果里位置越靠后,因此优先级越高(后者覆盖前者)。

### 约束
- 整条链累计不超过 `project_doc_max_bytes`(默认 32 KiB),
- 到上限就停止追加;
备注:
当达到上限时，可以如下解决:
- 提高限制(修改`config.toml`的`project_doc_max_bytes`选项)
- 将指令拆分到嵌套目录中

### 总结
每个会话一次、全局取一份(有且非空), 项目逐层各取一份(有且非空), 从根向下拼接, 越近越优先, 总量封顶 32 KiB。

## 二. 全局 AGENTS.md

### 通常包含
-可重复使用的偏好设置

### 备注
当需要临时覆盖全局`AGENTS.md`而无需删除`AGENTS.md`时，请使用 `~/.codex/AGENTS.override.md`,移除该覆盖文件即可复原。

## 三. 项目 AGENTS.md

### 通常包含
- 规范(norms)
- 预期(expectations)
- 子模块的特殊规则(覆盖上层规则)

### 备注
Codex 在到达当前目录后会停止搜索，因此请尽量将覆盖文件放置在专门工作目录附近。
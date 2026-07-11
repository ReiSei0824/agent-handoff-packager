# Smoke Test

- Skill: `agent-handoff-packager`
- Run date: 2026-07-11
- Overall result: `通过`

## 1. 结构检查

| 项目 | 结果 | 说明 |
| --- | --- | --- |
| frontmatter `name` 为 lowercase-hyphen | 通过 | `agent-handoff-packager` |
| `description` 50-150 字符 | 通过 | 长度将在脚本校验中复核 |
| `description` 以动词开头 | 通过 | `Builds ...` |
| 必要章节齐全 | 通过 | 核心定位 / 触发场景 / 工作流 / 输出格式 / Gotchas |
| 工作流 3-8 步 | 通过 | 共 6 步 |
| Gotchas 至少 4 条 | 通过 | 共 6 条 |
| 无未填充占位符 | 通过 | 已手查 |

## 2. README 检查

| 检查项 | 结果 | 说明 |
| --- | --- | --- |
| 安装路径与 skill 名一致 | 通过 | README 使用 `~/.claude/skills/agent-handoff-packager/` |
| 仓库名建议一致 | 通过 | 使用 `agent-handoff-packager` |
| 文件树存在且与目录一致 | 通过 | `SKILL.md` / `README.md` |
| 示例触发词与技能定位一致 | 通过 | 中英触发词都指向“交接包”而非执行本身 |

## 3. 触发干运行

### 中文触发词

输入：

```text
我想把下周的竞品周报交给 ChatGPT Work，但它老是返工。先帮我整理一个交接包，包含文件、边界和验收标准。
```

预期触发判断：

- 命中“交给 ChatGPT Work”“整理交接包”“文件、边界、验收标准”
- 应输出 handoff pack，而不是直接代做周报

输出骨架检查：

- 有 `任务摘要`
- 有 `输入材料`
- 有 `约束与红线`
- 有 `验收标准`
- 有 `可直接发送给代理的版本`

结论：`通过`

### English trigger

Input:

```text
Build me a handoff pack before I send this repo cleanup task to Codex. I need clear guardrails, checkpoints, and a done definition.
```

Expected trigger:

- Matches `handoff pack`, `send ... to Codex`, `guardrails`, `checkpoints`, `done definition`
- Should prepare a delegation brief, not start editing the repo

Output shape check:

- Contains deliverables
- Contains stop conditions
- Contains acceptance criteria
- Contains send-ready prompt

Conclusion: `通过`

## 4. 结果记录

- Smoke test status: `通过`
- Publish gate: `允许进入发布准备`
- 实际 GitHub 发布：`未执行`
- 原因：`gh` 读取 `C:\Users\49337\AppData\Roaming\GitHub CLI\config.yml` 时返回 Access is denied，本次不满足“环境允许且无需人工确认”的条件

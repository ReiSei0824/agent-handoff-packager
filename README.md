# Agent Handoff Packager

把“我想把这件事交给 AI 代理做”整理成一份可直接发送的交接包。它适用于 ChatGPT Work、Codex、Claude Code、Gemini 等多步骤代理场景，重点不是再写一个花哨提示词，而是把目标、文件、边界、检查点和验收标准讲清楚。

## 适用场景

- 要把研究、写作、代码、数据或运营任务委派给 AI 代理
- 任务已经不止一句话，开始涉及材料、文件、权限和风险
- 代理经常返工、越权、漏文件或做出“看起来努力但没交付”的结果

## 它会产出什么

- 一份结构化 `Agent Handoff Pack`
- 一段可直接复制给代理的发送版提示
- 明确的验收标准、停机线和中间检查点
- 对“不适合委派”的情况给出收缩建议

## 触发词

中文：

- “帮我整理一个交给 ChatGPT Work 的任务包”
- “先别执行，先把这件事写成 agent handoff”
- “我想把这个项目交给 Codex，先做交接说明”

English:

- “Build an agent handoff pack for this task”
- “Prepare a delegation brief before I send this to Codex”
- “Turn this into a handoff package for ChatGPT Work”

## 核心流程

1. 先判断任务是否适合委派，而不是默认一股脑外包给代理。
2. 盘点目标、材料、文件、权限和红线。
3. 写清 done definition、停机线和人工复核点。
4. 拆成阶段化执行节奏，避免一次性跑完全程。
5. 组装成可直接发送的 Markdown handoff pack。
6. 自检是否还存在模糊目标、缺文件或错误授权。

## 输出示例

```markdown
# Agent Handoff Pack

## 任务摘要
- 任务：整理一份 SaaS 竞品对比周报
- 建议委派给：ChatGPT Work

## 输入材料
- `pricing-notes.xlsx`
- `customer-calls.md`
- `https://example.com/competitor-a`

## 约束与红线
- 不要伪造价格
- 没查到的指标标注“待验证”

## 验收标准
1. 输出一张对比表
2. 给出 3 条可执行判断
3. 每条结论都带来源
```

## 安装方式

推荐安装目录：

```text
~/.claude/skills/agent-handoff-packager/
├── SKILL.md
└── README.md
```

本机本次自动化生成的工作目录是：

```text
C:\Users\49337\.claude\skills\代理交接包设计师（agent-handoff-packager）\
```

如果要发布到 GitHub，仓库名建议使用 `agent-handoff-packager`，README 保持与前置安装目录一致，不要把中文本地目录名写成安装路径。

## 发布说明

- 当前版本已包含标准 `SKILL.md` 和 README。
- 发布前建议先做一次真实触发词 smoke test，确认输出会直接落成 handoff pack，而不是停在抽象建议层。
- 若环境内 `gh` 或认证异常，先保留本地文件并生成 `publish-checklist.md`，不要强推或覆盖已有仓库。

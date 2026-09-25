# learn-anything

A Codex skill for progressive, personalized learning with homework tracking.

一个用于渐进式、个性化学习并跟踪作业的 Codex 技能。

---

## What It Does / 功能介绍

`learn-anything` turns Codex into a structured tutor. Tell it "I want to learn X" and it guides you through:

`learn-anything` 将 Codex 变成结构化的导师。告诉它"我想学 X"，它会引导你完成：

1. **Intake / 摸底评估** — Multiple-choice assessment of your current knowledge, goals, and learning style / 通过多选题评估你当前的知识水平、目标和学习风格
2. **Planning / 制定计划** — A customized learning path broken into 5–10 minimum learnable units (MLUs) / 定制化的学习路径，拆分为 5–10 个最小可学单元
3. **Teaching / 渐进教学** — Each unit follows a fixed sequence: Motivation → Analogy → Intuition → Definition / 每个单元按固定顺序教学：动机 → 类比 → 直觉 → 定义
4. **Verification / 学习验证** — Socratic checks, hands-on practice, teach-back, active recall / 苏格拉底式检验、动手实践、反向教学、主动回忆
5. **Homework / 作业系统** — Auto-assigned after each phase with quantitative rubrics and remediation protocols / 每阶段自动布置作业，附带量化评分标准和补救协议
6. **Persistence / 进度持久化** — All progress saved to `D:\learn_anything_data\<topic>\` for seamless session resumption / 所有进度保存到 `D:\learn_anything_data\<topic>\`，可无缝续接

## Structure / 文件结构

```
learn-anything/
├── SKILL.md                          # Core instructions / 核心指令
├── README.md                         # This file / 本文件
├── agents/
│   └── openai.yaml                   # UI metadata / UI 元数据
├── references/
│   ├── methodology.md                # Teaching methodology & rubrics / 教学方法论与评分标准
│   └── homework.md                   # Homework specification & scoring / 作业规范与评分
└── assets/                           # Supporting files / 辅助文件目录
```

## Data Storage / 数据存储

Learning records are stored per topic / 每个主题独立存储学习记录：

```
D:\learn_anything_data\
└── <topic-slug>\
    ├── plan.md          # Approved learning plan / 确认后的学习计划
    ├── progress.md      # Session-by-session progress log / 每节课的进度日志
    ├── state.json       # Machine-readable state for resuming / 机器可读的续接状态
    └── assets/          # Topic-specific supporting files / 主题相关辅助文件
```

## Key Features / 核心特性

- **Quantitative rubrics / 量化评分标准** — Every homework uses 0–4 scoring criteria, eliminating subjective judgment / 所有作业使用 0–4 评分制，消除主观判断
- **Homework gates / 作业门禁** — Units are locked until their homework passes / 作业未通过则锁定下一单元
- **Dual-gate resume / 双重门禁续接** — Warm-up HW (recall) and Unit HW (application) are independent / Warm-up HW（回忆）与 Unit HW（应用）相互独立
- **Remediation protocol / 补救协议** — Up to 3 failures trigger escalating intervention（review → re-teach → mandatory review session）
- **Adaptive difficulty / 自适应难度** — Adjusts to user level（beginner → expert）and learning style（reading / hands-on / visual / mix）

## Installation / 安装

Copy the `learn-anything` folder to your Codex skills directory / 将 `learn-anything` 文件夹复制到 Codex skills 目录：

```bash
cp -r learn-anything $CODEX_HOME/skills/
```

Or clone this repo directly / 或直接克隆本仓库：

```bash
git clone https://github.com/L3702/learn-anything-skill.git $CODEX_HOME/skills/learn-anything
```

## Usage / 使用示例

```
You / 你: I want to learn Python decorators / 我想学 Python 装饰器
Codex: [Phase 0 intake → multiple-choice assessment / 摸底评估 → 多选题]
Codex: [Presents learning plan for approval / 展示学习计划等你确认]
You / 你: Looks good! / 看起来不错！
Codex: [Assigns Pre-study HW / 布置学前作业]
You / 你: [Submits HW / 提交作业]
Codex: [Unit 1 teaching → Socratic check → Hands-on → Recall test / 教学 → 检验 → 实践 → 回忆]
Codex: [Unit HW assigned, state.json saved / 布置单元作业，保存状态]
...
You / 你: Continue learning Python decorators / 继续学 Python 装饰器
Codex: [Reads state.json → Warm-up HW → resumes from checkpoint / 读取状态 → 热身作业 → 从检查点续接]
```
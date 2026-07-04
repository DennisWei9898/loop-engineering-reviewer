<div align="center">

# loop-engineering-reviewer

**A compliance reviewer for AI loop projects — audit against Loop Engineering, then fix while keeping your style.**
**AI 迴圈專案的合規審查員 —— 用 Loop Engineering 量尺體檢，再保留你的風格只修合規。**

Review your agent / skill / cron loop against seven Loop Engineering rules, then fix only the structure — never your voice.
用七條 Loop Engineering 量尺審你的 agent / skill / cron 迴圈，只修結構、不碰你的語氣。

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](#license)
![Claude Code](https://img.shields.io/badge/Claude%20Code-skill%20%2B%20subagent-8A2BE2.svg)
![Rubric](https://img.shields.io/badge/rubric-Loop%20Engineering-orange.svg)
![Mode](https://img.shields.io/badge/mode-review%20%2B%20fix-blue.svg)

**[English](#english)** · **[繁體中文](#繁體中文)**

</div>

---

<a name="english"></a>

## English

A reviewer built on Addy Osmani's [Loop Engineering](https://addyosmani.com/blog/loop-engineering/). Use it to **produce and review** an AI loop project (agent / skill / cron automation). It does two things:

1. **Review** — audits your project against seven Loop Engineering rules, gives `PASS / FAIL / WARN` + evidence from the source, and points to what to change.
2. **Fix** — after confirming with you, edits directly but **fixes only compliance and fully preserves your original style and opinions**. A check-up and a prescription, not a transfusion.

### Why you need it

As you wire more agents / skills / crons together, the thing that breaks isn't usually a feature bug — it's the **loop structure**:

- letting the writer grade its own homework (maker/verifier not separated)
- a gate that can't actually reject bad output ("take the highest of 3 rounds")
- a loop running unattended, failing unattended (Ralph Wiggum)
- an out-of-domain judge (a docs expert grading SEO claims)

This is the tool that hunts exactly those "loop structure diseases".

### The 80/20 questioning discipline

It won't dump 50 questions on you. When it finds a pile of issues:

1. it surfaces the **3–5 highest-impact** questions first (real bug > gate weakness > safety > the rest)
2. minor issues are fixed **when encountered** or batched later
3. it raises compliance to 100% **progressively**, reporting `X/7 → Y/7` each pass
4. if you insist on doing it all at once, it lists everything but **confirms one at a time** — never overloading you

### Install (skill, subagent, or both)

**As a Skill (Claude Code)**
```bash
mkdir -p ~/.claude/skills/loop-engineering-reviewer
cp SKILL.md ~/.claude/skills/loop-engineering-reviewer/SKILL.md
```
Then say "use loop-engineering-reviewer to audit this agent."

**As a Subagent (Claude Code)**
```bash
cp loop-engineering-reviewer.agent.md ~/.claude/agents/loop-engineering-reviewer.md
```
Then spawn the `loop-engineering-reviewer` subagent to run an audit in isolation.

> Skill = review + fix inline in the main chat. Agent = a fresh-context audit in its own session (closer to Loop Engineering's "verifier fresh context" ideal).

### The rubric: seven Loop Engineering rules

| # | Rule | In one line |
|---|---|---|
| L1 | Maker/Verifier separation | writer ≠ checker; the verifier is an independent fresh context |
| L2 | Objective gate | pass conditions are machine-checkable / re-runnable, not "looks good" |
| L3 | Minimal viable loop, 4 parts | automation + skill + state file + a gate that can reject bad output |
| L4 | Stop point + iteration cap | round limits; no "take the highest score" softening |
| L5 | Human gate before irreversible | confirm before commit / push / publish / spend |
| L6 | Success metric = adoption rate | track how often output is accepted, not just tokens |
| L7 | Guard the three traps | silent failure / comprehension debt / cognitive surrender |

### Credit

The rubric is entirely from Addy Osmani's [Loop Engineering](https://addyosmani.com/blog/loop-engineering/) (also on O'Reilly Radar). This tool just lands it as a runnable review flow.

### License

MIT — use, modify, and share freely.

---

<a name="繁體中文"></a>

## 繁體中文

一個建立在 Addy Osmani《[Loop Engineering](https://addyosmani.com/blog/loop-engineering/)》上的**合規審查員**，用來幫你「產出並 review 一個 AI 迴圈專案」（agent / skill / cron 自動化）。它做兩件事：

1. **審** —— 用七條 Loop Engineering 量尺逐條檢查你的專案，給 `PASS / FAIL / WARN` + 原文證據，指出要改哪裡。
2. **改** —— 跟你確認後直接動手修，但**只修合規性、完整保留你的原始風格與觀點**。體檢後開藥，不是換血。

### 為什麼你會需要它

你把 agent / skill / cron 越串越多之後，最容易壞的不是功能 bug，而是**迴圈結構**：

- 讓寫的人自己改自己的作業（maker/verifier 沒分離）
- gate 其實否決不了爛輸出（「3 輪取最高分」這種軟化）
- 迴圈無聲地一直跑、一直錯（Ralph Wiggum）
- 拿領域外的裁判去審（用文件專家審 SEO 主張）

這支就是專門抓這類「loop 結構病」的體檢工具。

### 八二法則提問紀律

它不會一次拋 50 個問題壓垮你。發現一堆問題時：

1. 先挑**影響最大的 3–5 個**關鍵問題（真 bug > gate 命門 > 安全 > 其餘）
2. 細碎的問題**遇到再改**或分批
3. **循序漸進**把合規度拉到 100%，每批回報 `X/7 → Y/7` 進度
4. 你若堅持一次到位，它會列全部，但**逐一確認**，不一次塞爆你的認知

### 安裝（skill、subagent，擇一或都裝）

**當 Skill（Claude Code）**
```bash
mkdir -p ~/.claude/skills/loop-engineering-reviewer
cp SKILL.md ~/.claude/skills/loop-engineering-reviewer/SKILL.md
```
之後說「用 loop-engineering-reviewer 審一下這個 agent」即可觸發。

**當 Subagent（Claude Code）**
```bash
cp loop-engineering-reviewer.agent.md ~/.claude/agents/loop-engineering-reviewer.md
```
之後 spawn `loop-engineering-reviewer` subagent 在獨立 context 跑審查。

> Skill 版 = 在主對話裡順手審＋改。Agent 版 = 丟進獨立 context 跑一份審查（更貼近 Loop Engineering 的 verifier fresh context）。

### 量尺：Loop Engineering 七條

| # | 量尺 | 一句話 |
|---|---|---|
| L1 | Maker/Verifier 分離 | 寫的人 ≠ 審的人，verifier 獨立 fresh context |
| L2 | Gate 客觀可判 | 過閘條件是機器可判/可重跑，不是「看起來不錯」 |
| L3 | 最小可行迴圈四零件 | 自動化 + skill + 狀態檔 + 一道能否決爛輸出的關卡 |
| L4 | 有停止點 + 迭代上限 | 有輪次上限，禁止「取最高分放行」軟化閘門 |
| L5 | 不可逆前人工閘 | commit/push/發布/花錢前拿人類確認 |
| L6 | 成功指標＝採納率 | 記錄產出被採納的比例，不是只看 token |
| L7 | 防三大陷阱 | 無聲失敗 / 理解債 / 認知投降 各有對策 |

### 致謝

量尺全部來自 Addy Osmani 的《[Loop Engineering](https://addyosmani.com/blog/loop-engineering/)》（O'Reilly Radar 亦有轉載）。本工具只是把它落地成一份可執行的審查流程。

### 授權

MIT —— 自由使用、修改、分享。

---

<div align="center">
<sub>Rubric source · 量尺來源：Addy Osmani <a href="https://addyosmani.com/blog/loop-engineering/">Loop Engineering</a></sub>
</div>

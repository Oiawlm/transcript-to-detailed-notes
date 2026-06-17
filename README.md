[中文](#中文) | [English](#english)

---

## 中文

# Transcript to Detailed Notes

一个 [Agent Skill](https://agentskills.io)，把原始口述文字稿（直播、会议、讲座、采访）变成**高质量结构化笔记**——不是框架式总结。

### 解决的问题

大多数 AI 总结工具给 2 小时的视频产出 5 句话概述，所有实质内容都丢了。这个 skill 反过来：**去噪音，留实质**。

### 功能

- 清理口头语言（口水话、重复、碎句）为干净书面表达
- 保留所有实质内容：论点、数据、案例、结论
- 按主题分节（不按时间顺序）
- 智能处理问答段落（问题浓缩，回答完整保留）
- 自动存入 Obsidian vault（如果已配置）

### 安装

```bash
npx skills add Oiawlm/transcript-to-detailed-notes
```

### 使用

1. 给对方你的文字稿文件路径
2. Agent 自动读取、分段、提取、合并
3. 输出：按主题整理的结构化 markdown 笔记

触发词：「处理文字稿」「整理文字稿」「detailed notes」「直播总结」

### 效果示例

**处理前（原始口述）：**
> 就是说呢就是我们这个产品它最核心的点啊，就是它能够自动地去呃就是把你的一些重复性的工作给它自动化掉，嗯这个其实是很多用户反馈的一个痛点嘛，就是他们每天要花很多时间在处理一些重复的事情上，然后我们做了这个功能之后呢，就是用户的时间节省了大概40%左右。

**处理后：**
> 产品的核心功能是自动处理重复性工作。这是用户反馈的主要痛点——每天花大量时间在重复事务上。上线后用户时间节省约 40%。

所有信息保留，语言清洁，实质不变。

### 实际案例

[ai-course-notes](https://github.com/Oiawlm/ai-course-notes) —— 直播文字稿 + 结构化笔记。

### 支持平台

- Claude Code
- Hermes Agent
- Codex CLI
- 任何支持 [agentskills.io](https://agentskills.io) 标准的 agent

### 许可证

MIT

---

## English

# Transcript to Detailed Notes

An [Agent Skill](https://agentskills.io) that turns raw oral transcripts (live streams, meetings, lectures, interviews) into **detailed structured notes** — not shallow summaries.

### The Problem

Most AI summarization tools give you a 5-sentence overview of a 2-hour talk. All the substance is lost. This skill does the opposite: **eliminate noise, preserve substance**.

### What It Does

- Cleans up oral language (filler words, repetition, broken sentences) into clean written form
- Preserves ALL substantive content: arguments, data points, examples, conclusions
- Structures output by topic (not chronological transcript order)
- Handles Q&A sections intelligently (condense questions, preserve complete answers)
- Auto-saves to Obsidian vault if configured

### Install

```bash
npx skills add Oiawlm/transcript-to-detailed-notes
```

### Usage

1. Drop your transcript file path
2. The agent reads, chunks, extracts, and merges
3. Output: structured markdown notes organized by topic

Trigger phrases: "process this transcript", "整理文字稿", "detailed notes", "直播总结"

### Before / After

**Before (raw oral transcript):**
> 就是说呢就是我们这个产品它最核心的点啊，就是它能够自动地去呃就是把你的一些重复性的工作给它自动化掉，嗯这个其实是很多用户反馈的一个痛点嘛，就是他们每天要花很多时间在处理一些重复的事情上，然后我们做了这个功能之后呢，就是用户的时间节省了大概40%左右。

**After (processed):**
> 产品的核心功能是自动处理重复性工作。这是用户反馈的主要痛点——每天花大量时间在重复事务上。上线后用户时间节省约 40%。

All information preserved. Language cleaned. Substance identical.

### See It In Action

Real examples: [ai-course-notes](https://github.com/Oiawlm/ai-course-notes) — transcripts + structured notes.

### Platforms

- Claude Code
- Hermes Agent
- Codex CLI
- Any agent supporting the [agentskills.io](https://agentskills.io) standard

### License

MIT

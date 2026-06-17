# Transcript to Detailed Notes

An [Agent Skill](https://agentskills.io) that turns raw oral transcripts (live streams, meetings, lectures, interviews) into **detailed structured notes** — not shallow summaries.

## The Problem

Most AI summarization tools give you a 5-sentence overview of a 2-hour talk. All the substance is lost. This skill does the opposite: **eliminate noise, preserve substance**.

## What It Does

- Cleans up oral language (filler words, repetition, broken sentences) into clean written form
- Preserves ALL substantive content: arguments, data points, examples, conclusions
- Structures output by topic (not chronological transcript order)
- Handles Q&A sections intelligently (condense questions, preserve complete answers)
- Auto-saves to Obsidian vault if configured

## Install

```bash
npx skills add Oiawlm/transcript-to-detailed-notes
```

Or manually:

```bash
git clone https://github.com/Oiawlm/transcript-to-detailed-notes.git
cp -r transcript-to-detailed-notes ~/.claude/skills/
```

## Usage

1. Drop your transcript file path
2. The agent reads, chunks, extracts, and merges
3. Output: structured markdown notes organized by topic

Trigger phrases: "process this transcript", "整理文字稿", "detailed notes", "直播总结"

## Before / After

**Before (raw oral transcript):**
> 就是说呢就是我们这个产品它最核心的点啊，就是它能够自动地去呃就是把你的一些重复性的工作给它自动化掉，嗯这个其实是很多用户反馈的一个痛点嘛，就是他们每天要花很多时间在处理一些重复的事情上，然后我们做了这个功能之后呢，就是用户的时间节省了大概40%左右。

**After (processed):**
> 产品的核心功能是自动处理重复性工作。这是用户反馈的主要痛点——每天花大量时间在重复事务上。上线后用户时间节省约 40%。

All information preserved. Language cleaned. Substance identical.

## Platforms

- Claude Code
- Hermes Agent
- Codex CLI
- Any agent supporting the [agentskills.io](https://agentskills.io) standard

## License

MIT

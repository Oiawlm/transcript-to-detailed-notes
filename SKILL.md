---
name: transcript-to-detailed-notes
description: Use when the user provides a transcript file (live stream recording, meeting, lecture, interview) and wants detailed structured notes — not a shallow summary. Triggers on phrases like "process this transcript", "整理文字稿", "detailed notes", "直播总结".
---

# Transcript to Detailed Notes

Turn raw oral transcripts into high-quality structured notes. The goal is **extraction and refinement**, not compression.

## Core Principle

**Eliminate noise, preserve substance.** Oral language has filler, repetition, broken sentences. Your job: clean it up into written language WITHOUT losing any arguments, data, examples, or conclusions. If the original makes 10 substantive points, the output must have all 10 — just in better language.

## Workflow

### Phase 1: Load the transcript

Ask the user for the file path. Read it with `read_file`. If it exceeds ~2000 lines, read in chunks (offset/limit).

### Phase 2: Chunk

If the transcript is under ~8000 characters, process it in one pass.

If longer, split into chunks of ~4000 characters each, with ~400 character overlap between chunks. Process each chunk independently through Phase 3, then merge results in Phase 4.

### Phase 3: Extract per chunk

For each chunk, produce a detailed extraction (NOT a summary). Follow these rules:

**For every paragraph/segment:**

- **Narrative/monologue:** Extract ALL substantive content — viewpoints, reasoning chains, data, examples, case studies, conclusions. Reword from oral to written style: remove filler words (um, you know, 就是说, 那个), fix broken sentences, eliminate repetition. Do NOT delete arguments.

- **Q&A (question + answer):**
  - Condense the **question** to its core meaning (1-2 sentences max).
  - Preserve the **answer** fully — clean up language only. Do not delete any substantive points in the answer.

- **Fluff/banter/off-topic:** Skip entirely. If the speaker is making small talk, greeting viewers, or talking about irrelevant topics, omit it.

**What to KEEP (do not delete):**
- Specific data, numbers, statistics
- Named entities (people, companies, products, tools)
- Concrete examples and case studies
- Reasoning chains (because X → Y → Z)
- Actionable advice and steps
- Contrasts and comparisons (A vs B)
- Controversial or nuanced positions

**What to REMOVE:**
- Filler words (um, uh, like, 嗯, 那个, 就是)
- Verbatim repetition (same point said 3 times → keep once, refined)
- False starts and self-corrections
- Off-topic banter
- Viewer greetings and thanks
- Tangents that go nowhere

**Language quality:**
- Broken oral sentences → complete written sentences
- Colloquial expressions → standard written language (but keep the speaker's voice)
- Vague pronouns → specific references when clear

### Phase 4: Merge and structure

After processing all chunks, merge the extractions into a single structured document:

1. **Identify themes/topics** across all chunks
2. **Group related content** under topic headings
3. **Resolve overlaps** — if two chunks cover the same topic, merge them
4. **Organize** in logical order (not chronological transcript order)

Output format:

```markdown
# [Title — infer from content]

## 主题一：[topic name]

[Detailed, structured content here. Preserve all substance.]

## 主题二：[topic name]

### Q&A

**Q:** [condensed question]
**A:** [polished but complete answer, all points preserved]

## 主题三：[topic name]

...
```

### Phase 5: Save and offer to publish

Save to `~/AppData/Local/hermes/transcript-notes/[inferred-title].md`. If Obsidian vault is configured (OBSIDIAN_VAULT_PATH env var), also copy there under a `Transcript-Notes/` folder.

After saving, proactively ask the user: "要发布到课程笔记仓库吗？" If yes, invoke `publish-course-notes` skill.

## Quality Gate (before showing to user)

Re-read the output and verify:
- [ ] Are there fewer substantive points than the original? → FAIL, go back
- [ ] Does it read like a framework/overview? → FAIL, add more detail
- [ ] Is any data point, name, or example missing? → FAIL, add it back
- [ ] Is the language clean (no "um", "就是说")? → Good
- [ ] Are Q&A questions condensed but answers complete? → Good

## Example

**Before (transcript excerpt):**
> 就是说呢就是我们这个产品它最核心的点啊，就是它能够自动地去呃就是把你的一些重复性的工作给它自动化掉，嗯这个其实是很多用户反馈的一个痛点嘛，就是他们每天要花很多时间在处理一些重复的事情上，然后我们做了这个功能之后呢，就是用户的时间节省了大概40%左右。

**After (processed):**
> 产品的核心功能是自动处理重复性工作。这是用户反馈的主要痛点——每天花大量时间在重复事务上。上线后用户时间节省约 40%。

All information preserved. Language cleaned. Word count reduced but substance identical.

## Pitfalls

- **Don't mechanically chunk-and-forget.** For transcripts under ~150KB, read the entire thing first to build a thematic mental model, then extract. Mechanical chunk processing loses cross-references and topic threads that span sections.
- **Use structural markers.** Speaker labels, timestamps, and natural pauses are section boundaries. Use them to identify topic shifts rather than cutting at arbitrary character counts.
- **Reorganize, don't transcribe.** Chronological transcript order is rarely the best structure. Speakers jump between topics — you should regroup by theme.
- **Oral→written is not just deleting words.** Some oral expressions carry nuance (tone, emphasis, hedging) that pure text loses. If the speaker is being cautious or uncertain, preserve that signal.

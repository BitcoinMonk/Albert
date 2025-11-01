---
description: Quick memory note - remember this specific thing
---

# Note - Quick Memory Capture

You are Albert, capturing a quick memory note. This is for rapid context capture without a full session save.

## Usage

User says: `/note <some important thing>`

Examples:
- `/note decided to use PostgreSQL for better transaction support`
- `/note bug in auth.ts line 45 needs fixing after demo`
- `/note client wants dark mode feature in next sprint`

## Protocol

### 1. Determine Note Type

Based on the content, decide if this is:
- **Decision**: An architectural or technical decision
- **Task**: Something to do later
- **Insight**: A learning or pattern observed
- **Context**: General project information

### 2. Store Appropriately

**For Decisions/Insights:**
- Append to `~/.claude/albert/memory/insights/quick-notes.md` with timestamp
- Format: `## [YYYY-MM-DD HH:MM] - [Note]`

**For Tasks:**
- Append to `~/.claude/albert/memory/context/current.md` under "Quick Notes" section
- Format: `- [ ] [Note] (added YYYY-MM-DD)`

**For Context:**
- Append to `~/.claude/albert/memory/context/current.md` under "Notes" section
- Format: `- [YYYY-MM-DD] [Note]`

### 3. Acknowledge

Respond with:
- "Noted: [brief confirmation of what was captured]"
- "I'll remember that [brief context]"
- Simple, quick acknowledgment

### 4. Update Current Context

Update the timestamp in `~/.claude/albert/memory/context/current.md` to reflect the note was added.

## Example Flow

**User**: `/note switching to Redis for caching instead of Memcached`

**Albert**:
1. Identifies this as a decision/insight
2. Appends to `insights/quick-notes.md`:
   ```
   ## 2025-11-01 08:45 - Cache Technology Decision
   Switching to Redis for caching instead of Memcached.
   ```
3. Responds: "Noted: switching to Redis for caching. I'll remember this decision."

## Design Philosophy

Quick notes are:
- **Fast**: Minimal friction to capture important info
- **Organized**: Sorted by type for easy retrieval
- **Timestamped**: Know when things were noted
- **Lightweight**: Don't require full session protocol

They complement full session saves (`/remember`) by capturing ephemeral but important context during work.

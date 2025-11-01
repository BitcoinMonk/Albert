# Albert's Memory System

This directory contains Albert's memory system - a scalable, queryable structure designed for both immediate use and future integration with MCP servers or databases.

## Architecture

```
memory/
├── sessions/          # Individual session logs
├── activities/        # Project activities & milestones
├── insights/          # Accumulated wisdom & patterns
├── context/           # Current working context
└── README.md          # This file
```

## Directory Structure

### sessions/
**Purpose:** Chronological record of each work session

**Files:** `YYYY-MM-DD.md` or `YYYY-MM-DD-topic.md`

**Contains:** What was accomplished, decisions made, code changes, next steps

**Query examples:**
- "What did we work on last Tuesday?"
- "Show me all October sessions"
- "Find the session where we decided on the database schema"

### activities/
**Purpose:** Project milestones and significant activities

**Files:** `YYYY-MM-DD_activity-name.md`

**Contains:** Goals, progress, technical details, outcomes

**Query examples:**
- "Show me the API refactoring activity"
- "What activities are still in progress?"
- "List all completed milestones"

### insights/
**Purpose:** Long-term learnings, patterns, and architectural wisdom

**Files:** `topic-name.md` (thematic, not chronological)

**Contains:** Principles discovered, best practices, patterns to follow/avoid

**Query examples:**
- "What have we learned about authentication?"
- "Show me our architecture decisions"
- "What patterns do we follow for error handling?"

### context/
**Purpose:** Albert's working memory - what's happening RIGHT NOW

**Files:** `current.md`

**Contains:** Active focus, immediate tasks, recent sessions, open questions

**Access:** Albert reads this FIRST on every session start for immediate context

## File Naming Conventions

| Type | Format | Example |
|------|--------|---------|
| Session | `YYYY-MM-DD.md` | `2025-10-31.md` |
| Session (named) | `YYYY-MM-DD-topic.md` | `2025-10-31-initial-setup.md` |
| Activity | `YYYY-MM-DD_topic.md` | `2025-10-31_agent-system.md` |
| Insight | `topic-name.md` | `architecture-decisions.md` |
| Context | `current.md` | `current.md` (only one) |

## Setup for New Users

When cloning this repository:

```bash
cd albert/memory

# Sessions directory (creates your first session file from template)
cp sessions/.template.md sessions/$(date +%Y-%m-%d).md

# Context is already created, but you can reset it
cp context/.template.md context/current.md  # Optional: only if you want a fresh start

# Activities and insights are created as needed
```

## Git Strategy

**What's tracked:**
- ✅ Directory structure (`.gitkeep` files)
- ✅ Template files (`.template.md`)
- ✅ This README

**What's ignored (personal):**
- ❌ Your session files
- ❌ Your activity files
- ❌ Your insight files
- ❌ Your context file

**Why:** Each team member maintains their own personal memory with Albert. The structure is shared, the content is private. No merge conflicts, no pollution of teammates' context.

## How Albert Uses This

### At Session Start:
1. **Read `context/current.md`** - Get immediate working context
2. **Check latest session** - See what happened last time
3. **Scan recent activities** - Understand current project state
4. **Review relevant insights** - Apply accumulated wisdom

### During Session:
- **Update `context/current.md`** - Maintain current state
- **Note insights** - Capture new learnings in `insights/`

### At Session End (`/close` command):
1. **Create session file** - `sessions/YYYY-MM-DD.md` with full session record
2. **Update activities** - Progress on ongoing work
3. **Capture insights** - New patterns or decisions
4. **Refresh context** - Update `current.md` for next session
5. **Git commit** - Preserve personal memory state

## Future: MCP Server Integration

This structure is designed for future queryability:

```javascript
// Query by date range
mcp.query("albert/memory/sessions", {
  from: "2025-10-01",
  to: "2025-10-31"
})

// Query by topic
mcp.query("albert/memory/insights", {
  topic: "architecture"
})

// Get current context
mcp.read("albert/memory/context/current")
```

## Future: SQLite Integration

Structure maps naturally to tables:

```sql
CREATE TABLE sessions (
  date TEXT PRIMARY KEY,
  duration INTEGER,
  summary TEXT,
  content TEXT
);

CREATE TABLE activities (
  id TEXT PRIMARY KEY,
  date TEXT,
  topic TEXT,
  status TEXT,
  content TEXT
);

CREATE TABLE insights (
  topic TEXT PRIMARY KEY,
  category TEXT,
  created TEXT,
  updated TEXT,
  content TEXT
);
```

## Benefits of This Structure

1. **Scalable**: Grows indefinitely without cluttering
2. **Queryable**: Easy to search by date, topic, or type
3. **Future-proof**: Ready for MCP/database integration
4. **Clean git**: Folders tracked, contents private
5. **Organized**: Clear separation of concerns
6. **Immediately useful**: Simple file-based system works today

---

*This memory system makes Albert more than a chatbot - it makes him your persistent project companion.*

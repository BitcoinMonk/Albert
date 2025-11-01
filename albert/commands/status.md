---
description: Show current focus, active work, and recent activity
---

# Status - Current State Overview

You are Albert, providing a status overview of current work and context.

## Protocol

### 1. Read Current Context

Read `~/.claude/albert/memory/context/current.md` to understand:
- Active focus
- Current tasks
- Open questions
- Recent notes

### 2. Check Recent Activity

List recent session files:
```bash
ls -lt ~/.claude/albert/memory/sessions/*.md 2>/dev/null | head -3
```

Read the most recent session (just the summary section) to understand latest work.

### 3. Review Active Activities

Check for in-progress activities:
```bash
grep -l "Status.*in-progress" ~/.claude/albert/memory/activities/*.md 2>/dev/null
```

If any exist, read their current status sections.

### 4. Compile Status Report

Provide a concise overview in this format:

```
## Current Status

**Active Focus**: [from current.md]

**Recent Work** (last session on [date]):
- [Key accomplishment 1]
- [Key accomplishment 2]

**In Progress**:
- [Active activity 1]
- [Active activity 2]

**Next Steps**:
- [Next step 1]
- [Next step 2]

**Open Questions**:
- [Question 1 if any]

**Last Session**: [X days/hours ago]
```

### 5. Be Concise

Keep the status report:
- **Brief**: 5-10 lines max unless there's significant context
- **Actionable**: Focus on what's next, not just what was done
- **Relevant**: Prioritize current information over historical

## Example Outputs

### Active Project
```
## Current Status

**Active Focus**: Implementing user authentication system

**Recent Work** (yesterday):
- Set up JWT token generation
- Created login/logout endpoints

**In Progress**:
- Password reset flow
- Email verification

**Next Steps**:
- Add rate limiting to auth endpoints
- Write integration tests

**Last Session**: 1 day ago
```

### Between Projects
```
## Current Status

**Active Focus**: Between projects, exploring new tech stack

**Recent Work** (3 days ago):
- Completed e-commerce platform
- Deployed to production

**Next Steps**:
- Start planning for next project
- Research React Server Components

**Last Session**: 3 days ago
```

### No Recent Activity
```
## Current Status

**Active Focus**: No current focus set

**Last Session**: 2 weeks ago (worked on API refactoring)

**Suggestion**: Ready to start fresh? Use `/recall` for a full recap, or just tell me what you'd like to work on today.
```

## Design Philosophy

The status command is:
- **Quick**: Fast overview without deep dive
- **Oriented**: Shows direction and momentum
- **Current**: Focuses on now and next, not past
- **Actionable**: Suggests what to do next

Use `/status` for a quick "where are we?" check.
Use `/recall` for a deeper "how did we get here?" exploration.

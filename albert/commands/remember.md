---
description: Save current session state and remember everything
---

# Remember Session

You are Albert, saving the current session to memory. Follow this protocol:

## 1. Review Current Session

Read `~/.claude/albert/memory/context/current.md` to understand what happened this session and what's currently active.

## 2. Create Session File

Create a new session file: `~/.claude/albert/memory/sessions/[YYYY-MM-DD].md`

If multiple sessions happen in one day, use: `~/.claude/albert/memory/sessions/[YYYY-MM-DD]-N.md`

Include:
- Date and duration
- Summary of what was accomplished
- Decisions made and why
- Code changes
- Insights and learnings
- Blockers encountered
- Next steps

Use the template at `~/.claude/albert/memory/sessions/.template.md` as a guide (if it exists).

## 3. Update Activities

If working on a specific project activity:
- Update or create file in `~/.claude/albert/memory/activities/[YYYY-MM-DD]_[activity-name].md`
- Update progress, status, and outcomes
- Use the template at `~/.claude/albert/memory/activities/.template.md` if creating new (if it exists)

## 4. Capture Insights

If any important patterns, principles, or decisions emerged:
- Create or update files in `~/.claude/albert/memory/insights/[topic-name].md`
- Document the insight, context, and rationale
- Use the template at `~/.claude/albert/memory/insights/.template.md` if creating new (if it exists)

## 5. Update Current Context

Update `~/.claude/albert/memory/context/current.md` with:
- Latest focus and active tasks
- Reference to the session file just created
- Open questions or blockers
- What to pick up next session

## 6. Optional: Commit Changes

If the user has initialized git in their Albert memory directory, offer to create a commit:

```bash
cd ~/.claude/albert
git add memory/
git commit -m "Albert session save: [brief description]"
```

Only do this if `.git` exists in `~/.claude/albert/`.

## 7. Farewell

Provide user with:
- Brief summary of session accomplishments
- Key decisions or milestones reached
- Suggested next steps for next session
- Friendly sign-off

---

**Remember:** This new memory structure is designed for scalability. Each session gets its own file, insights accumulate in thematic files, and context stays current. This makes Albert's memory queryable and ready for future MCP/database integration.

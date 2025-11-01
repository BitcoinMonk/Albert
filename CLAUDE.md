# CLAUDE.md

**Instructions for Claude Code when working in the Albert Installer Repository**

## Critical Understanding

**This repository is an INSTALLER, not Albert himself.**

- This repo contains: Templates, setup scripts, documentation
- Albert (the actual agent) lives in: `~/.claude/agents/albert.md` (after installation)
- Albert's memory lives in: `~/.claude/albert/memory/` (after installation)
- This repo should remain: Generic, machine-independent, shareable

**Your role:** Help users install their own personal Albert agent.

## When User Asks for Installation Help

### 1. Detect Operating System

Check the platform:
- Windows: Use `setup-global.ps1`
- Linux/Mac: Use `setup-global.sh`

### 2. Guide Installation

**For Windows:**
```powershell
.\scripts\setup-global.ps1
```

**For Linux/Mac:**
```bash
chmod +x scripts/setup-global.sh
./scripts/setup-global.sh
```

### 3. Explain What Happens

The setup script:
- Creates `~/.claude/agents/albert.md` (agent definition)
- Creates `~/.claude/albert/memory/` (memory structure)
- Initializes git repo in `~/.claude/albert/` for backup (optional)
- User now has Albert available globally via `@albert`

### 4. After Installation

Tell the user:
```
Albert is now installed! You can:
1. Use @albert in any project
2. Optionally delete this installer repo (but keep it if you want to reinstall/update later)
3. Your Albert lives in ~/.claude/agents/albert.md
4. Your memories are in ~/.claude/albert/memory/
```

## Repository Purpose

This repository serves THREE audiences:

### 1. End Users (Installing Albert)
- Clone repo → Run setup → Get personal Albert
- One-time process
- Can delete repo after installation

### 2. Developers (Improving Albert)
- Edit templates in `albert/templates/`
- Improve setup scripts in `scripts/`
- Update documentation
- Commit improvements for everyone

### 3. Self (Claude Code in this repo)
- Read this file to understand your role
- Help users with installation
- Guide development of Albert's templates
- Ensure repo stays generic and shareable

## What To Never Do

❌ **Never add user-specific paths** to templates
- Use `%USERPROFILE%` (Windows) or `~` (Linux/Mac)
- Templates must work for ANY user on ANY machine

❌ **Never commit personal memories** to this repo
- Memory files are .gitignored
- Personal data stays in `~/.claude/albert/memory/`

❌ **Never assume this repo IS Albert**
- This repo creates Albert
- Albert lives elsewhere after installation

## Project Structure

```
albert/                        # THIS REPO (installer)
├── .claude/
│   └── agents/albert.md       # Template/demo Albert (for this repo only)
├── albert/
│   ├── ALBERT.md              # Core principles (generic)
│   ├── templates/
│   │   └── albert.md   # Template for ~/.claude/agents/albert.md
│   └── memory/templates/      # Memory structure templates
├── scripts/
│   ├── setup-global.ps1       # Windows installer
│   └── setup-global.sh        # Linux/Mac installer
├── SETUP.md                   # User installation guide
├── CLAUDE.md                  # This file (instructions for you)
└── README.md                  # End-user overview
```

**After user runs setup:**
```
~/.claude/agents/
└── albert.md                  # User's personal Albert agent

~/.claude/albert/memory/               # User's personal memory (NOT in this repo)
├── sessions/
├── projects/
├── insights/
└── context/
```

## The Two-Phase Vision

### Phase 1 (Current): Claude Code Subagent
- Albert is a specialized agent within Claude Code
- This repo distributes the template
- Users install Albert as a personal Claude Code agent
- Albert uses Claude's AI model with custom prompts

### Phase 2 (Future): Independent AI Assistant
- Albert gets his own local AI model
- Becomes independent of Claude
- This repo becomes full Albert installer (like Claude install)
- For now, keep this vision in mind but focus on Phase 1

## Development Workflow

### User Wants to Install Albert

**Your Response:**
1. Confirm they're in the Albert installer repo
2. Detect their OS (Windows/Linux/Mac)
3. Run the appropriate setup script via Bash tool
4. Verify installation by checking for `~/.claude/agents/albert.md`
5. Explain how to use `@albert` in any project

### User Wants to Improve Albert's Template

**Your Response:**
1. Understand what they want to change
2. Edit `albert/templates/albert.md` (the template)
3. Ensure changes are machine-independent
4. Test the changes (they can reinstall to test)
5. Document the improvement

### User Wants to Add Features

**Your Response:**
1. Add to `albert/ALBERT.md` if it's core behavior
2. Update `albert/templates/albert.md` if it's agent-specific
3. Create new memory templates if needed
4. Update documentation (README, SETUP)
5. Ensure everything stays generic

## Common User Questions

**Q: "Is Albert installed?"**
A: Check if `~/.claude/agents/albert.md` exists. If yes, Albert is installed. If no, run the setup script.

**Q: "How do I use Albert?"**
A: After installation, use `@albert` in any Claude Code session in any project.

**Q: "Can I customize Albert?"**
A: Yes! Edit `~/.claude/agents/albert.md` (your personal Albert) to customize behavior for yourself. Edit templates in THIS repo to improve Albert for everyone.

**Q: "Where are my memories?"**
A: In `~/.claude/albert/memory/` on your machine. This is separate from this installer repo.

**Q: "Do I need to keep this repo?"**
A: No, you can delete it after installation. But keeping it lets you reinstall or update Albert later.

## Self-Prompting Setup

When a user opens Claude Code in this repo and asks:
```
"Help me install Albert"
```

You should:
1. Read SETUP.md for detailed instructions
2. Detect their operating system
3. Offer to run the setup script for them
4. Execute: `.\scripts\setup-global.ps1` (Windows) or `./scripts/setup-global.sh` (Linux/Mac)
5. Verify installation completed successfully
6. Explain how to use `@albert` anywhere

## Best Practices

✅ **Do:**
- Keep templates generic (use environment variables)
- Test changes on multiple platforms
- Update documentation when changing behavior
- Explain the installer vs installed distinction clearly

❌ **Don't:**
- Hardcode user-specific paths
- Commit personal memory files
- Assume this repo is where Albert lives
- Make OS-specific changes without handling all platforms

## Testing Changes

Before committing template changes:
1. User can reinstall Albert: Run setup script again (it will ask to overwrite)
2. Test on target platform (Windows/Linux/Mac)
3. Verify Albert works after installation
4. Check that no personal data leaked into repo

## Git Strategy

**In This Repo (Committed):**
- Agent templates
- Setup scripts
- Documentation
- Core principles
- Memory templates (empty, for initialization)

**In This Repo (Ignored):**
- `albert/memory/*` (except templates)
- Any user-specific data
- Local configuration overrides

**Not In This Repo (User's Machine):**
- `~/.claude/agents/albert.md` (created by setup)
- `~/.claude/albert/memory/` (created by setup, user's private data)

## Success Criteria

You've succeeded when:
- ✅ User has `~/.claude/agents/albert.md` installed
- ✅ User has `~/.claude/albert/memory/` initialized
- ✅ User can use `@albert` in any project
- ✅ User understands this repo is just the installer
- ✅ No personal data committed to this repo

## Remember

**This repo is the blueprint. Albert is the house built from it.**

Each user builds their own house (Albert) using this blueprint. They can customize their house, but improvements to the blueprint should be shared back to this repo.

---

**Your Mission:** Help users create their own personal Albert assistant by guiding them through installation and ensuring this repository remains a clean, generic, shareable template.

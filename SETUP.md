# Albert Installation Guide

Welcome! This guide will help you install Albert, your personal AI assistant for Claude Code.

## Important: What You're Installing

**This repository is an installer.** Running the setup creates:
- `~/.claude/agents/albert.md` - Albert's agent definition
- `~/.albert/memory/` - Albert's memory system

After installation, you can use `@albert` in any project. You can even delete this installer repo if you want.

## Prerequisites

- [Claude Code](https://claude.ai/code) installed and working
- Git installed
- Windows (PowerShell) OR Linux/Mac (Bash)

## Installation Options

### Option 1: Let Claude Install Albert (Easiest)

1. **Clone this repository:**
   ```bash
   git clone https://github.com/your-org/albert.git
   cd albert
   ```

2. **Open Claude Code:**
   ```bash
   claude
   ```

3. **Ask Claude to help:**
   ```
   @claude Please read SETUP.md and install Albert globally for me
   ```

Claude will:
- Detect your operating system (Windows/Linux/Mac)
- Run the appropriate setup script
- Verify installation
- Explain how to use Albert

### Option 2: Manual Installation

1. **Clone this repository:**
   ```bash
   git clone https://github.com/your-org/albert.git
   cd albert
   ```

2. **Run the setup script for your platform:**

   **Windows (PowerShell):**
   ```powershell
   .\scripts\setup-global.ps1
   ```

   **Linux/Mac (Bash):**
   ```bash
   chmod +x scripts/setup-global.sh
   ./scripts/setup-global.sh
   ```

3. **Verify installation:**
   ```bash
   # Check that Albert was installed
   ls ~/.claude/agents/albert.md
   ls ~/.albert/memory/
   ```

## What the Setup Script Does

The installation script:

1. **Creates `~/.claude/agents/albert.md`**
   - This is Albert's agent definition
   - Claude Code reads this to know how Albert behaves
   - Located where Claude Code looks for agents

2. **Creates `~/.albert/memory/` structure:**
   ```
   ~/.albert/memory/
   ├── sessions/          # Session logs
   ├── projects/          # Per-project insights
   ├── insights/          # Universal learnings
   └── context/           # Current focus
   ```

3. **Initializes git repository**
   - Your memory is git-initialized for backup
   - Stays local (no remote by default)
   - You control if/where to sync

4. **Creates initial memory files**
   - `context/current.md` - Current working context
   - `insights/architecture.md` - Architecture patterns
   - `insights/patterns.md` - Universal patterns

## Using Albert

### First Use

After installation, Albert is available everywhere:

```bash
cd ~/any-project
claude
```

In Claude Code:
```
@albert Hello! I'm working on a new authentication service.

Albert: Hello! Let me check my notes... This appears to be our first
conversation about this project. Tell me about your authentication
service - what are you trying to achieve?
```

### During Development

```
@albert Should I use JWT or sessions for this API?

Albert: Good question. Let's think through the tradeoffs...
[Provides architectural guidance]
```

Albert maintains context throughout your session.

### Ending a Session

```
/close

Albert: Session saved! Summary:
- Discussed authentication strategy
- Decided on JWT with refresh tokens
- Next: Implement token refresh logic

Memory updated. See you next time!
```

### Resuming Work

```
@albert I'm back

Albert: Welcome back! It's been 2 days since we last worked together.
On Oct 29th, we were designing the authentication service. You'd
decided on JWT with refresh tokens and were about to implement the
refresh logic. Ready to continue?
```

## Directory Structure

### This Installer Repo (What You Cloned)

```
albert/                    # Installer repository
├── .claude/
│   └── agents/albert.md   # Template/demo (works in this repo)
├── albert/
│   ├── ALBERT.md          # Core principles
│   ├── templates/
│   │   └── global-albert.md    # Template for ~/.claude/agents/albert.md
│   └── memory/templates/       # Memory structure templates
├── scripts/
│   ├── setup-global.ps1        # Windows installer
│   └── setup-global.sh         # Linux/Mac installer
├── SETUP.md                    # This file
└── README.md                   # Overview
```

### After Installation (Your Home Directory)

```
~/.claude/agents/
└── albert.md              # Your personal Albert agent

~/.albert/memory/           # Your personal memory
├── sessions/              # Session logs
│   └── 2024-10-31.md
├── projects/              # Per-project insights
│   └── my-project/
│       ├── overview.md
│       └── decisions.md
├── insights/              # Universal learnings
│   ├── architecture.md
│   ├── patterns.md
│   └── tradeoffs.md
└── context/
    └── current.md         # Current working context
```

## Customizing Albert

### For Yourself

Edit your personal Albert:
```bash
# Edit agent behavior
nano ~/.claude/agents/albert.md

# Review/edit memories
cd ~/.albert/memory
```

### For Everyone (Template)

Edit the installer template:
```bash
# Edit the template
cd /path/to/albert-installer
nano albert/templates/global-albert.md

# Commit and share
git commit -am "Improved Albert's behavior"
git push
```

## Commands

- **`@albert [question]`** - Invoke Albert
- **`/close`** - Save session and update memory
- **`/restore`** - Restore context from previous session

## Platform-Specific Notes

### Windows
- Setup script: `setup-global.ps1` (PowerShell)
- Albert installed at: `C:\Users\YourName\.claude\agents\albert.md`
- Memory location: `C:\Users\YourName\.albert\memory\`
- Uses `%USERPROFILE%` environment variable

### Linux/Mac
- Setup script: `setup-global.sh` (Bash)
- Albert installed at: `~/.claude/agents/albert.md`
- Memory location: `~/.albert/memory/`
- May need: `chmod +x scripts/setup-global.sh`

## Backup Your Memories

Your memories are git-initialized. To back up to a private remote:

```bash
cd ~/.albert
git remote add origin https://github.com/yourusername/albert-memory-private.git
git push -u origin master
```

⚠️ **Use a PRIVATE repository** - your memories are personal!

## Sync Across Machines

**Machine 1 (first setup):**
```bash
# Install Albert
./scripts/setup-global.sh

# Push memories to private remote
cd ~/.albert
git remote add origin <your-private-repo>
git push -u origin master
```

**Machine 2 (sync from Machine 1):**
```bash
# Install Albert (creates empty memory)
./scripts/setup-global.sh --skip-git

# Replace with your synced memory
rm -rf ~/.albert
git clone <your-private-repo> ~/.albert
```

## Troubleshooting

### "Albert not found"

**Problem:** `@albert` doesn't work

**Solutions:**
1. Check if installed: `ls ~/.claude/agents/albert.md`
2. If missing, run setup script again
3. Restart Claude Code
4. Try: `@claude show available agents`

### "Memory not saving"

**Problem:** Albert doesn't remember previous sessions

**Solutions:**
1. Check memory directory exists: `ls ~/.albert/memory/`
2. Check write permissions: `ls -la ~/.albert/`
3. Use `/close` explicitly before ending session
4. Check git status: `cd ~/.albert && git status`

### "Can I reinstall?"

**Answer:** Yes! Run the setup script again. It will ask if you want to overwrite the existing installation. Your memories in `~/.albert/memory/` are preserved.

### "Setup script fails"

**Windows:**
- Run PowerShell as Administrator
- Enable script execution: `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser`

**Linux/Mac:**
- Make executable: `chmod +x scripts/setup-global.sh`
- Check bash is installed: `which bash`

## Uninstalling Albert

To remove Albert:

```bash
# Remove agent definition
rm ~/.claude/agents/albert.md

# Remove memories (backup first!)
rm -rf ~/.albert
```

To reinstall later, just run the setup script again.

## What's Next?

After installation:

1. **Start using Albert:** Open Claude Code in any project, use `@albert`
2. **Customize if desired:** Edit `~/.claude/agents/albert.md`
3. **Optionally delete installer:** You don't need this repo anymore (unless you want to update/reinstall later)
4. **Optional backup:** Push `~/.albert/` to private git remote

## Team Usage

Each team member:
1. Clones this installer repo
2. Runs setup script
3. Gets their own Albert + private memory
4. Can customize independently

**Result:** Everyone has Albert, but with their own personal memories.

## Getting Help

- **Installation issues:** Open an issue in this repository
- **Using Albert:** Try `@albert help` or read `albert/ALBERT.md`
- **Claude Code:** https://docs.claude.com/en/docs/claude-code

## The Vision

**Phase 1 (Now):** Albert is a Claude Code subagent
- Persistent, context-aware personal assistant
- Works across all your projects
- Private, local-first memory

**Phase 2 (Future):** Albert becomes independent
- His own local AI model
- Full installer like Claude
- This repo evolves into the distribution

---

**Ready to install?** Run the setup script for your platform!

**Questions?** See README.md or open an issue.

**Want to improve Albert?** Edit the templates and contribute back!

# Albert Installer

**A Personal AI Assistant for Claude Code**

This repository is an **installer** that helps you create your own personal AI assistant named Albert. Albert will live in your Claude Code environment as a persistent, context-aware agent that remembers your work across all projects.

## Important: What This Repo Is (and Isn't)

**This repo is:**
- ✅ A template and setup tool
- ✅ Cloned once to install Albert
- ✅ Shareable with your team
- ✅ Generic and machine-independent

**This repo is NOT:**
- ❌ Albert himself (he lives in `~/.claude/agents/` after setup)
- ❌ A place to store your personal memories
- ❌ Something you work in daily

**Workflow:** Clone → Run Setup → You now have Albert → (Optionally delete this repo)

## What is Albert?

Albert is a Claude Code subagent that:
- 🧠 **Remembers** - Maintains context across sessions, days, weeks
- 🎯 **Guides** - Provides architectural insights and asks the right questions
- 📝 **Documents** - Tracks decisions and builds knowledge over time
- 🔄 **Adapts** - Learns your patterns and preferences through memory

## Quick Start

### 1. Clone This Repo (One Time)

```bash
git clone https://github.com/your-org/albert.git
cd albert
```

### 2. Let Claude Setup Albert for You

Open Claude Code in this directory:

```bash
claude
```

Then say:
```
@claude Please read SETUP.md and help me install Albert globally
```

Claude will detect your operating system and run the appropriate setup.

**OR** manually run the setup script:

**Windows:**
```powershell
.\scripts\setup-global.ps1
```

**Linux/Mac:**
```bash
chmod +x scripts/setup-global.sh
./scripts/setup-global.sh
```

### 3. Start Using Albert

After setup, Albert is available everywhere:

```bash
cd ~/my-project
claude
```

In Claude Code:
```
@albert Let's review the architecture of this system
```

## Where Does Albert Live?

After installation:

```
~/.claude/agents/
└── albert.md              # Albert's agent definition (Claude Code reads this)

~/.claude/albert/memory/    # Albert's personal memory (Albert writes here)
├── sessions/              # Session logs
├── activities/            # Project milestones
├── insights/              # Universal learnings
└── context/current.md     # Current focus
```

**Key Points:**
- `.claude/agents/` is where Claude Code looks for agents
- `.claude/albert/memory/` is where Albert stores his memories
- Both are in YOUR home directory, not in this repo
- Your memories are private and stay on your machine

## How Albert Works

### Session Start
```
User: @albert Hello

Albert:
Good morning! I checked my notes from yesterday. We were working on
the authentication service. You'd decided on JWT tokens and were
about to implement rate limiting. Ready to continue?
```

### During Work
Albert maintains context, asks probing questions, and tracks decisions.

### Session End
```
User: /remember

Albert:
Session saved! Summary:
- Implemented rate limiting with token bucket
- Decided on Redis for token storage
- Next: Add monitoring for rate limit hits

Memory updated. See you next time!
```

## The Two-Phase Vision

### Phase 1 (Now): Claude Code Subagent
- Albert is a specialized agent within Claude Code
- Uses Claude's AI model but with custom prompts
- Maintains persistent memory across sessions
- Available via `@albert` in any project

### Phase 2 (Future): Independent AI Assistant
- Albert gets his own local AI model
- Becomes independent of Claude
- Full installer like Claude itself
- This repo evolves into the Albert distribution

**For now:** Focus is making the best Claude Code assistant possible.

## What Gets Installed

The setup script creates:

1. **Global Agent** (`~/.claude/agents/albert.md`)
   - Albert's agent definition
   - Read by Claude Code to know how Albert behaves
   - Contains Albert's instructions and protocols

2. **Memory Structure** (`~/.claude/albert/memory/`)
   - Your personal knowledge base with Albert
   - Git-initialized for backup (stays local)
   - Grows over time as you work with Albert

3. **Nothing Else**
   - No always-running services
   - No cloud connections
   - No telemetry
   - Completely local and private

## Features

- **Time-Aware**: Knows if it's been hours, days, or weeks since last session
- **Context-Rich**: Maintains project state, decisions, and open questions
- **Proactive**: Suggests next steps and catches potential issues
- **Architectural**: Thinks in systems and patterns, not just solutions
- **Private**: All memory stays on your machine

## Commands

Once Albert is installed:

- `@albert [question]` - Invoke Albert in any conversation
- `/remember` - Save session state before ending
- `/recall` - Restore and review context from previous sessions
- `/note <text>` - Quick memory note (remember this specific thing)
- `/status` - Show current focus and recent activity

## Directory Structure

**This Installer Repo:**
```
albert/                    # The repo you cloned
├── .claude/
│   └── commands/          # Slash commands for Claude Code
├── albert/
│   ├── ALBERT.md          # Core principles
│   ├── templates/         # Agent templates
│   └── memory/templates/  # Memory structure templates
├── scripts/
│   ├── setup-global.ps1   # Windows installer
│   └── setup-global.sh    # Linux/Mac installer
├── SETUP.md               # Detailed setup guide
└── README.md              # This file
```

**After Installation (Your Home Directory):**
```
~/.claude/agents/
└── albert.md              # Your personal Albert agent

~/.claude/albert/memory/
├── sessions/              # Your session logs
├── activities/            # Your project milestones
├── insights/              # Your learnings
└── context/current.md     # Your current focus
```

## Requirements

- [Claude Code](https://claude.ai/code) installed and working
- Git (for memory backup)
- Windows (PowerShell) or Linux/Mac (Bash)

## For Teams

Each team member:
1. Clones this repo
2. Runs setup to get their own Albert
3. Gets their own private memory
4. Can customize their Albert independently

**Result**: Everyone has the same Albert template but their own personal memories and customizations.

## FAQ

**Q: Do I need to keep this repo after installation?**
A: No. After setup, Albert lives in `~/.claude/agents/`. You can delete this repo. (But you might want to keep it to reinstall or update Albert later)

**Q: Can I customize Albert?**
A: Yes! Edit `~/.claude/agents/albert.md` to change his behavior. Edit `albert/ALBERT.md` in this repo if you want to change the template for others.

**Q: Where is my data stored?**
A: In `~/.claude/albert/memory/` on your machine. It never leaves your computer unless you explicitly sync it to a private git remote.

**Q: Can I use Albert in multiple projects?**
A: Yes! Albert is global. Use `@albert` in any project and he'll maintain context across all of them.

**Q: What if I want project-specific memory?**
A: Albert maintains project context through activity files and session notes, organizing them by date and topic in the memory directory.

**Q: Is this open source?**
A: Yes! MIT License. Contribute improvements back to help everyone's Albert get better.

**Q: Can Albert work without Claude Code?**
A: Not yet. That's Phase 2. For now, Albert requires Claude Code to function.

## Documentation

- **[SETUP.md](SETUP.md)** - Detailed installation guide
- **[albert/ALBERT.md](albert/ALBERT.md)** - Albert's core principles and behavior
- **[CLAUDE.md](CLAUDE.md)** - Instructions for Claude Code when helping with setup

## Contributing

Improve Albert for everyone:
1. Fork this repo
2. Make improvements to templates, setup scripts, or docs
3. Test on your platform
4. Submit pull request

## License

MIT License - Use freely, share improvements

## Credits

- Inspired by the wisdom of Albert Einstein and the humble rubber duck
- Built for the Claude Code agent system
- Created by developers who wanted their AI to remember yesterday

---

**Ready?** Clone this repo and run `./scripts/setup-global.sh` (or `.ps1` on Windows)

**Questions?** See [SETUP.md](SETUP.md) for detailed instructions

**Want to understand how Albert works?** See [albert/ALBERT.md](albert/ALBERT.md)

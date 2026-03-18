# 🦞 Claw Skills

OpenClaw Agent Skills Repository

This repository contains custom skills for OpenClaw AI agents.

## 📦 Installed Skills

| Skill | Description |
|-------|-------------|
| `agent-browser` | Fast Rust-based headless browser automation CLI with Node.js fallback |
| `find-skills` | Discover and install agent skills from ClawHub |
| `proactive-agent` | Transform AI agents into proactive partners with WAL Protocol, Working Buffer, and Autonomous Crons |
| `searxng` | Privacy-respecting metasearch using local SearXNG instance |
| `self-improving-agent` | Captures learnings, errors, and corrections for continuous improvement |
| `skill-vetter` | Security-first skill vetting before installation |

## 🚀 Usage

Skills are automatically loaded by OpenClaw from the `skills/` directory.

### Install a new skill

```bash
# Using ClawHub CLI
clawhub install <skill-name>

# Or manually clone into skills/ directory
git clone <skill-repo> skills/<skill-name>
```

### Create a new skill

1. Create a new directory in `skills/`
2. Add `SKILL.md` with skill description and instructions
3. Add any supporting scripts, assets, or documentation
4. Commit and push to this repository

## 📝 Structure

```
skills/
├── skill-name/
│   ├── SKILL.md          # Required: Skill definition and instructions
│   ├── scripts/          # Optional: Supporting scripts
│   ├── assets/           # Optional: Images, templates, etc.
│   └── README.md         # Optional: Skill-specific documentation
```

## 🔗 Links

- [OpenClaw Documentation](https://docs.openclaw.ai)
- [ClawHub](https://clawhub.com) - Discover and share skills
- [OpenClaw GitHub](https://github.com/openclaw/openclaw)

## 📄 License

Individual skills may have different licenses. Check each skill's directory for details.

---

Maintained by @zhangruke

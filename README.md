# Claude Code Skills

A collection of [Claude Code](https://claude.ai/code) slash command skills for confidential containers development workflows.

## Available Skills

| Skill | Invocation | Description |
|---|---|---|
| [cloud-api-adaptor](./cloud-api-adaptor/) | `/cloud-api-adaptor` | Set up, build, and test cloud-api-adaptor with libvirt locally (amd64, Ubuntu 24.04 podvm via mkosi) |

## Installation

### Prerequisites

- [Claude Code](https://claude.ai/code) CLI installed
- `~/.claude/commands/` directory (created automatically by Claude Code)

### Install a single skill

```bash
git clone https://github.com/confidential-devhub/claude-skills
cp claude-skills/<skill-name>/<skill-name>.md ~/.claude/commands/
```

### Install all skills

```bash
git clone https://github.com/confidential-devhub/claude-skills
for skill_dir in claude-skills/*/; do
    skill_name=$(basename "$skill_dir")
    cp "$skill_dir/$skill_name.md" ~/.claude/commands/
done
```

Claude Code picks up files in `~/.claude/commands/` automatically — no restart required.

### Keep skills up to date

```bash
cd claude-skills
git pull
# Re-run the copy commands above
```

## Usage

Once installed, invoke a skill with its slash command in any Claude Code session:

```
/cloud-api-adaptor setup
/cloud-api-adaptor build --debug
/cloud-api-adaptor test --filter TestLibvirtCreatePeerPod
```

Run any skill with no arguments for an interactive prompt.

## Contributing

Each skill lives in its own directory:

```
<skill-name>/
├── <skill-name>.md   # The skill file (YAML frontmatter + Markdown body)
└── README.md         # Human-readable docs for the skill
```

The skill file frontmatter must include `name`, `description`, `argument-hint`, and `allowed-tools`. Use an existing skill as a template, then open a pull request.

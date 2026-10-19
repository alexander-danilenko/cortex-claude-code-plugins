<h1 align="center">
  <img src="./assets/banner.svg" width="100%" alt="Cortex — Claude Code Plugin Marketplace" />
</h1>

<p align="center">
  <a href="https://github.com/alexander-danilenko/cortex-claude-code-plugins/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License: MIT" />
  </a>
</p>

> 🚀 A marketplace of small, focused Claude Code plugins. Install the ones you need and stop re-explaining how you write code.

This repository is a Claude Code plugin marketplace. Each plugin bundles a few related skills for one domain, such as web development, testing, or Jira reporting. You pick the plugins that fit your work. Nothing else gets loaded.

## 💡 Why Cortex

Most AI assistants will happily generate _something_. Getting them to write code _your_ way, with your conventions, architecture, and trade-offs, usually means re-explaining yourself every session or letting CLAUDE.md balloon out of control.

Cortex is what I built after I got tired of doing that. It is a collection of personal preferences, project scars, and team rules that I have gathered over the years. Each one is packaged as a skill, so Claude can reach for the right one on its own. Fork it, gut half of it, swap mine for yours. That is the point.

## ✨ How It Works

Install a plugin and it brings everything it needs: its skills, plus any hooks it ships. Once the plugin is installed and enabled, they trigger automatically. Each skill describes when it should fire, and Claude Code loads whichever ones match what you are doing:

- Open a `.tsx` file → the **react** and **typescript** skills kick in.
- Edit a NestJS controller → **nestjs** brings the module, DI, guard, and DTO rules.
- Ask for tests → **cortex-testing:conventions** picks the right unit, integration, or E2E approach.
- Draft API docs → **documentation** handles the voice and OpenAPI structure.
- Wrap up a ticket → **report-comment** writes the Jira update from your commits.
- Solve a tricky bug → **learn-with-docs** saves the lesson in `docs/solutions/`, so the next session does not rediscover it.

There is nothing to paste at the start of a session and nothing to repeat on a fresh repo. To turn a plugin off, disable it. You can also call any skill yourself with `/<plugin>:<skill>`, for example `/cortex-web:react`.

## 📚 Plugins

Browse the [`plugins/`](./plugins) directory to see what is inside. It has two groups:

- [`plugins/common`](./plugins/common) — plugins useful in any project, such as writing and communication.
- [`plugins/engineering`](./plugins/engineering) — plugins for languages, frameworks, testing, documentation, Jira, code review, and legacy modernization.

Every plugin folder has its own `skills/` directory with one folder per skill. Open a `SKILL.md` to see what it does, then install the plugins that fit your needs. All plugin names start with `cortex-`, so they do not clash with third-party plugins. Each plugin folder has the same name as its plugin, for example `plugins/engineering/cortex-web`.

Some plugins depend on others. Claude Code installs those dependencies for you.

## 📦 Installation

Add the marketplace once:

```bash
claude plugin marketplace add alexander-danilenko/cortex-claude-code-plugins
```

Then install the plugins you want. Use the plugin folder name:

```bash
claude plugin install cortex-communication@cortex-claude-code-plugins
claude plugin install cortex-web@cortex-claude-code-plugins
```

Claude will pull in the right skills as you work and keep them updated.

## 🛠️ Development

To load one plugin from a local clone (session-only):

```bash
claude --plugin-dir /path/to/cloned/repo/plugins/<group>/<plugin>
```

To make the whole marketplace persistent, register the clone as a local marketplace in `~/.claude/settings.json`:

```json
{
  "extraKnownMarketplaces": {
    "local": {
      "source": {
        "source": "directory",
        "path": "/path/to/cloned/repo"
      }
    }
  }
}
```

Then install a plugin once:

```bash
claude plugin install <plugin>@local
```

After pulling new changes, update it with:

```bash
claude plugin update <plugin>@local
```

## 🙏 Credits

[Jeffallan/claude-skills](https://github.com/Jeffallan/claude-skills) inspired me to start this project.

## 🤝 Contributing

These plugins reflect a personal workflow, so fork freely and adapt them to yours.

When you add or update a skill, use the [`skill-creator` plugin](https://claude.com/plugins/skill-creator) so it matches the expected format and conventions. Put it in the plugin that fits its domain, and bump that plugin's version in its `plugin.json`.

## License

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

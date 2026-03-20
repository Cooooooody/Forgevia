# Forgevia

Forge your agent workflow into steel.

Forgevia is a GitHub-first workflow bundle for agent-driven development. It combines:

- OpenSpec
- superpowers
- requesting-code-review
- playwright-interactive

Forgevia currently supports Codex only. Claude is not supported yet and will be added later.

The current first release path is Codex-first. Forgevia installs and manages a curated set of files under `~/.codex`, including:

- a top-level `forgevia` skill
- `playwright-interactive`
- Forgevia-managed overrides for selected superpowers skills

## Current Codex Scope

Forgevia currently assumes:

- `openspec` comes from `npm install -g @fission-ai/openspec@latest`
- `superpowers` is installed from upstream first
- Forgevia then directly overlays its managed customizations into `~/.codex`
- Forgevia does not own project business files; it only helps invoke `openspec init` when needed

## Managed Superpowers Overrides

Forgevia currently owns customized copies of:

- `brainstorming`
- `writing-plans`
- `subagent-driven-development`
- `requesting-code-review`
- `executing-plans`

These are customized for an OpenSpec-oriented workflow rooted in `openspec/changes/<change-name>/...`.

## Codex Quick Start

1. Install OpenSpec if needed:

```bash
npm install -g @fission-ai/openspec@latest
```

2. Install upstream superpowers for Codex:

Fetch and follow instructions from [superpowers Codex INSTALL](https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.codex/INSTALL.md)

3. Run the Forgevia installer:

```bash
./scripts/install-codex.sh
```

4. Check the managed state:

```bash
./scripts/doctor-codex.sh
```

5. In Codex, explicitly invoke Forgevia when you want the full orchestrated workflow:

```text
use Forgevia
```

6. When a repository has not been initialized for OpenSpec yet:

```bash
./scripts/bootstrap-project.sh --tools codex /path/to/project
```

## Key Files

- Codex install guide: [INSTALL.codex.md](INSTALL.codex.md)
- Codex manifest: [manifests/codex.json](manifests/codex.json)
- Forgevia skill: [assets/codex/skills/forgevia/SKILL.md](assets/codex/skills/forgevia/SKILL.md)

## Status

This repository is still being assembled. The current state provides:

- vendored Codex assets
- a machine-readable Codex manifest
- a minimal Codex installer
- a minimal Codex doctor
- a project bootstrap entrypoint that only runs `openspec init` when needed

Claude support is planned for a later phase in the same repository, but it is not implemented yet.

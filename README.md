# Agents Catalog

This repository acts as a machine-readable catalog for `AgentSync`.  
It is part of a management system to store and share skills, agents, and prompts between devboxes and/or teams.

> Refer to the [AgentSync project](https://github.com/gianni-rg/agents-sync-tool) documentation for more details on how to use the catalog and the CLI tool.
>
> *The project is in early stages of development, so expect breaking changes and improvements in the future.*

Assets can be consumed in GitHub Copilot CLI, VS Code, or other agentic coding harnesses.

- `agents-catalog` stores reusable assets and metadata. Ideally you have one (or more) centralized, *potentially private*, catalog repository for your team and/or organization.
- `AgentSync` installs and syncs them deterministically.

This repository is an *example* of such a catalog, and you should clone and copy its structure to create your own.

## Using with `AgentSync`

Examples from executing *within* a target repo:

```powershell
cd C:\Projects\my-application-repo

# List all assets in a local catalog
AgentSync list --catalog C:\Projects\my-agents-catalog

# Install an agent from the catalog to the current folder
AgentSync use custom-agent-1 --type agent --catalog C:\Projects\my-agents-catalog --local .

# Sync all assets from the catalog to the current folder
AgentSync sync --catalog C:\Projects\my-agents-catalog --local .
```

## `catalog.json` format

The repository uses JSON as the catalog format.

```json
{
  "version": 1,
  "targets": {
    "copilot": {
      "repo": {
        "agents": ".github/agents",
        "prompts": ".github/prompts",
        "skills": ".github/skills"
      }
    }
  },
  "catalog": {
    "agents": [],
    "prompts": [],
    "skills": [],
    "instructions": []
  }
}
```

Each entry describes:

- what the asset is
- where the source lives
- what it depends on
- which targets it can be installed into

## VS Code user path mapping

Quick reference for user-level customizations by OS:

- Windows: `%APPDATA%\\Code\\User` (for example `agents`, `prompts`, `skills`, `instructions`)
- Linux: `~/.config/Code/User`
- macOS: `~/Library/Application Support/Code/User`

This repository's `catalog.json` uses the Windows `%APPDATA%\\Code\\User` base for the `vscode.user` target.

## Contribution

The project is constantly evolving and contributions are warmly welcomed.

I'm more than happy to receive any kind of contribution to this experimental project: from helpful feedbacks to bug reports, documentation, usage examples, feature requests, or directly code contribution for bug fixes and new and/or improved features.

Feel free to file issues and pull requests on the repository and I'll address them as much as I can, *with a best effort approach during my spare time*. DO NOT expect a super fast turnaround, but I'll do my best to keep the project active and responsive.

> Development is mainly done on Windows, so other platforms are not directly developed, tested, or supported. Help is kindly appreciated in making the tool work on other platforms as well.

## Acknowledgements

Inspired by [The Library Meta-Skill](https://github.com/disler/the-library) and by the idea of having a structured way to share agents, skills, and prompts across projects and teams.

## License

This project is licensed under the [Apache License 2.0](./LICENSE).

Copyright © 2026 Gianni Rosa Gallina.

# AI Registry — GitHub (Inferred)

> **Inferred vendor repository.** This repo is maintained by the [AI Registry](https://github.com/eclipsefdn-ai-registry/ai-registry-core) project, not by GitHub. It pre-seeds the registry with GitHub's official MCP server, one first-party skill, and one first-party Agent Plugin.
>
> *This entry is based solely on information published through GitHub's official public channels. GitHub has not endorsed, approved or validated this listing, and is not necessarily participating in the AI Registry.*

## What this repo contains

**MCP server**: [`github/github-mcp-server`](https://github.com/github/github-mcp-server) — "GitHub's official MCP Server" per its own repo description, owned by the verified `github` GitHub org, and live in the official MCP registry as `io.github.github/github-mcp-server`. Registry-listed, so no `metadata`/`config` fallback is needed.

**Agent Skill**: `spark-app-template`, from [`github/copilot-plugins`](https://github.com/github/copilot-plugins) at `plugins/spark/skills/spark-app-template`. `copilot-plugins` is GitHub's own marketplace repo (owned by `github`, described in its README as "the official GitHub Copilot plugins collection", `marketplace.json` owner is `GitHub <copilot@github.com>`). Most of its bundled plugins are explicitly attributed to Microsoft in that same `marketplace.json` (`workiq`, `fabric-*`, `power-*`, `cpp-language-server`, `build-perf-cpp` — the last one authored by two named Microsoft engineers even though it lives in this repo). The `spark` entry carries no such third-party author, its content matches [GitHub Spark](https://github.com/features/spark) (GitHub's own AI app-building product), and its commit history shows it was authored/reviewed directly by GitHub staff (e.g. `JasonEtco`, whose public profile lists `company: GitHub`) committing straight to `main`. On that basis it's included; `build-performance-analysis`, the other skill in this repo (nested under the Microsoft-attributed `build-perf-cpp` plugin), is excluded.

**Agent Plugin**: [`github/copilot-advanced-security-plugin`](https://github.com/github/copilot-advanced-security-plugin) — "The official GitHub Copilot Advanced Security plugin" per its own repo description, owned by the `github` org, no external author. Its `plugin.json` manifest lives at `.github/plugin/plugin.json` rather than at the plugin directory root — GitHub's actual Copilot Plugin convention differs here from the [agent-plugins.org](https://agent-plugins.org) layout this registry's consolidation pipeline expects (manifest alongside `skills/` and `mcp.json`). The approval's `source.path` points at `.github/plugin` so the manifest itself (`name`, `description`, `version`) is found and Phase 4 validation passes; because of the layout mismatch, sparse-checkout won't materialize the plugin's actual `skills/` (`dependency-scanning`, `secret-scanning`) or `.mcp.json`, so `containedSkills`/`containedMcpServers` will enrich as empty rather than reflecting the plugin's real contents. This is a known limitation of pointing this tool's plugin-source enrichment at GitHub's real-world directory layout, not an error in the approval itself.

**Excluded entirely**: [`github/awesome-copilot`](https://github.com/github/awesome-copilot) — its own README states it is "sourced from third-party developers" ("Community-contributed instructions, agents, skills, and configurations..."); no entry in it is GitHub's own first-party content, so nothing from it is approved here.

**A2A agents**: none found. No `agent_card.json`-conformant agent published by GitHub was located.

## Documentation

See the [Vendor Guide](https://github.com/eclipsefdn-ai-registry/ai-registry-core#vendor-guide) in the central repository for how vendor repos work, how to add approvals, and how validation runs.

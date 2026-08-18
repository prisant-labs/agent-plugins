# agent-plugins

Marketplace for [prisant-labs](https://github.com/prisant-labs) Claude Code plugins.

Add it once and every plugin published here becomes available, including ones added later.

```
/plugin marketplace add https://github.com/prisant-labs/agent-plugins
```

Then install what you want:

```
/plugin install nonfiction-studio@agent-plugins
```

## Available plugins

| Plugin | What it does | Status |
|---|---|---|
| [nonfiction-studio](https://github.com/prisant-labs/nonfiction-studio) | Turns Claude into a governed non-fiction book studio: specialist subagents, a plain-Markdown project bible, deterministic quality gates, and publishing compliance support. | Not yet public |
| [prisant-utilities](https://github.com/prisant-labs/prisant-utilities) | Session continuity (wrap and resume), structured analysis briefs, guide bundles, and cross-LLM peer review. Five skills, `plab-` prefix. | Available |

**Note on availability:** this marketplace is public, but a plugin listed here installs only once its own repository is public. An entry marked "Not yet public" above will fail to install until that happens. The listing is published early so the marketplace name is stable from the start.

## What this repo is

Only a pointer. It contains a single `.claude-plugin/marketplace.json` that names each plugin and the repository it lives in. No plugin code lives here, and each plugin keeps its own repository, versioning, issues, and CI.

Plugins may also carry a self-marketplace in their own repository, which is what makes local directory installs work during development. That is deliberate and does not conflict with this one: marketplace names are registered independently, so both can be added at the same time.

## License

MIT for this marketplace manifest. Each plugin carries its own license.

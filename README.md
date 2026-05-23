# Ronen's Claude Code Marketplace

A small marketplace of Claude Code plugins for working with npm. Add it once and install either (or both) plugins.

## Install

```
/plugin marketplace add RonenMars/claude-marketplace
```

Then install whichever you want:

```
/plugin install npm-registry-manager@ronenmars
/plugin install npm-package-owner@ronenmars
```

## Plugins

### [npm-registry-manager](https://github.com/RonenMars/npm-registry-manager)

Manage *which* npm registry you talk to. Switch between public npm, GitHub Packages, private/enterprise registries, and regional mirrors (taobao, tencent, huawei, yarn, etc.). Bind npm scopes (`@org`) to registries, configure auth via env-var references, and verify your setup. An `nrm`/`grm` replacement that needs only `npm` for core operations.

```
/npm-use taobao
/npm-scope set @acme https://npm.corp.internal/
/npm-query exists @acme/my-pkg corp
```

### [npm-package-owner](https://github.com/RonenMars/npm-package-owner)

Manage *your published* npm packages. Pre-publish safety checks, a guarded publish flow (plan → confirm → execute), download statistics, and package health overviews.

```
/npm-preflight
/npm-publish patch
/npm-downloads one-more-highlight last-month
/npm-stats one-more-highlight
```

## How they fit together

| | npm-registry-manager | npm-package-owner |
|---|---|---|
| Concern | *Which* registry, auth, scopes | *What you do* with published packages |
| Mutates | `.npmrc` config | publishes packages (with confirmation) |

registry-manager gets you authenticated and pointed at the right registry; package-owner publishes and tracks. Use them together or independently.

## Architecture

This marketplace catalog references each plugin from its own repository via `github` sources, so the catalog and the individual plugins version independently. Each plugin repo is self-contained and can also be installed directly:

```
/plugin marketplace add RonenMars/npm-registry-manager
/plugin marketplace add RonenMars/npm-package-owner
```

But adding this consolidated marketplace is simpler — one command exposes both.

## License

MIT — see each plugin repository for its own LICENSE.

# ship

**ship** is the Krewire ecosystem's plugin and third-party integration registry.

## Packages

- **plugin** — Plugin system for site build extensions (Tailwind CSS, etc.)
- **packages** — Generic package resolver chain (plugin → Go module → npm)

## Overview

ship provides the scalable plugin infrastructure used by `kiw build` and `kiw add/remove`:

- **Plugin interface** — Minimal contract for build-time extensions (Detect, Build)
- **Installer interface** — Optional contract for `kiw add/remove name@version`
- **Registry** — Self-registering plugin list via `init()`
- **Resolver chain** — plugin → gomod → npm resolution order for `kiw add/remove`

## Plugins Included

- **Tailwind CSS** — Detects `tailwind.config.js`, builds via Tailwind CLI, supports `kiw add tailwind` / `kiw remove tailwind`

## Usage

```go
import "github.com/krewire/ship/plugin"

// Register a custom plugin
func init() {
	plugin.Register(&MyPlugin{})
}

// Use resolver chain in kiw add/remove
import "github.com/krewire/ship/packages"

resolved, _ := packages.DefaultChain().Resolve(packages.ParseSpec("twcss@latest"))
resolved.Installer.Add(projectRoot, "latest")
```

## Architecture

Part of the Krewire unified framework vision ([KWF-M8K2Q](https://github.com/krewire/framework/blob/main/docs/specs/KWF-ARCH-M8K2Q-unified-framework-vision.md)).

The plugin system is designed to be:
- **Scalable** — New plugins require zero changes to kiw
- **Optional** — Build failures don't block the site build
- **Declarative** — Detected by config file presence at project root
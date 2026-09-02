# android-game-packages

A [sing-box](https://sing-box.sagernet.org/) `package_name` rule-set of Android
games, rebuilt weekly from the curated package lists maintained by
Magisk/KernelSU gaming-performance modules.

**1117 packages.**

## Use

```json
{
  "tag": "games",
  "type": "remote",
  "format": "binary",
  "url": "https://raw.githubusercontent.com/nxdomainx/android-game-packages/main/games-packages.srs",
  "download_detour": "direct",
  "update_interval": "168h"
}
```

Then reference `"rule_set": "games"` from a route rule.

`package_name` matching is **Android-only** — the match is made by the VPN
service, which knows which app owns a connection. Put this in a client config;
a server has no package information.

## Files

| file | what |
|---|---|
| `games-packages.srs` | compiled binary rule-set (`SRS` v2, reads on sing-box 1.10+) |
| `games-packages.json` | the same data as a source rule-set |
| `gamelist.txt` | plain package names, one per line |

## Licence

The package lists are aggregated from upstream projects, each under its own
licence. This repository claims no ownership of the underlying data.

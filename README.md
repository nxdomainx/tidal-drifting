# dist

Compiled [sing-box](https://sing-box.sagernet.org/) rule-sets, rebuilt on a
schedule and served straight from this repo.

## Available rule-sets

| name | type | entries | notes |
|---|---|---|---|
| `games` | `package_name` | 1117 | Android games, merged from curated gaming-module package lists |

Each rule-set ships three files:

| file | what |
|---|---|
| `<name>.srs` | compiled binary rule-set — this is the one you point sing-box at |
| `<name>.json` | the same data as a source rule-set |
| `<name>.txt` | plain entries, one per line |

## Use

```json
{
  "tag": "games",
  "type": "remote",
  "format": "binary",
  "url": "https://raw.githubusercontent.com/nxdomainx/dist/main/games.srs",
  "download_detour": "direct",
  "update_interval": "168h"
}
```

Then reference `"rule_set": "games"` from a route rule. sing-box refreshes it on
its own.

### Note on `package_name`

`package_name` matching is **Android-only** — the match is made by the VPN
service, which knows which app owns a connection. Put a package rule-set in a
client config; a server has no package information and will never match it.

## Licence

Data is aggregated from upstream projects, each under its own licence. This
repository claims no ownership of the underlying data.

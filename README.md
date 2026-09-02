# tidal-drifting

Compiled [sing-box](https://sing-box.sagernet.org/) rule-sets, rebuilt on a
schedule and served straight from this repo.

Only the compiled `.srs` ships here. Sources, build scripts and the plaintext
lists live elsewhere.

## Available rule-sets

| name | type | entries | notes |
|---|---|---|---|
| `games-android` | `package_name` | 6698 | Android games — Play Store top charts merged with curated gaming-module package lists |
| `music-apps-android` | `package_name` | 76 | Music, podcast and radio apps — every ID resolved against Play or an APK mirror |
| `geosite-category-music` | `domain_suffix` | 318 | Music/audio services — upstream music geosites plus the many services no upstream list covers |

## Use

```json
{
  "tag": "music",
  "type": "remote",
  "format": "binary",
  "url": "https://raw.githubusercontent.com/nxdomainx/tidal-drifting/main/geosite-category-music.srs",
  "download_detour": "direct",
  "update_interval": "168h"
}
```

Then reference `"rule_set": "music"` from a route rule. sing-box refreshes it on
its own.

### Note on `package_name`

`package_name` matching is **Android-only** — the match is made by the VPN
service, which knows which app owns a connection. Put a package rule-set in a
client config; a server has no package information and will never match it.

`geosite-category-music` has no such restriction: it is a domain rule-set and
works in node and front-end core profiles as well as clients.

### Note on ads

These are routing rule-sets, not blocklists. `geosite-category-music` matches on
domain suffixes, so a service's ad and telemetry hosts still match through the
parent domain. If you want those rejected, put a block rule ahead of this one.

## Licence

Data is aggregated from upstream projects, each under its own licence. This
repository claims no ownership of the underlying data.

# geoip

Public LelandJin GeoIP feed. Bytes are mirrored from [Loyalsoldier/geoip](https://github.com/Loyalsoldier/geoip) `release`. This repo does not rebuild the generator and does not use a MaxMind account.

## Public files

After the weekly Action publishes the `release` branch:

| File | URL |
| --- | --- |
| Country | https://raw.githubusercontent.com/LelandJin/geoip/release/Country.mmdb |
| Country checksum | https://raw.githubusercontent.com/LelandJin/geoip/release/Country.mmdb.sha256sum |
| ASN (mmdb) | https://raw.githubusercontent.com/LelandJin/geoip/release/Country-asn.mmdb |
| ASN checksum | https://raw.githubusercontent.com/LelandJin/geoip/release/Country-asn.mmdb.sha256sum |
| ASN (dat) | https://raw.githubusercontent.com/LelandJin/geoip/release/geoip-asn.dat |
| ASN dat checksum | https://raw.githubusercontent.com/LelandJin/geoip/release/geoip-asn.dat.sha256sum |

Upstream sources:

- https://raw.githubusercontent.com/Loyalsoldier/geoip/release/Country.mmdb
- https://raw.githubusercontent.com/Loyalsoldier/geoip/release/Country-asn.mmdb
- https://raw.githubusercontent.com/Loyalsoldier/geoip/release/geoip-asn.dat

## Clash / mihomo

Download `Country.mmdb` into the program directory, then:

```yaml
rules:
  - GEOIP,PRIVATE,DIRECT,no-resolve
  - GEOIP,CN,DIRECT,no-resolve
```

ASN files are for tools that look up organization / AS number, not country. Point those tools at `Country-asn.mmdb` or `geoip-asn.dat`.

## Sync

`.github/workflows/sync-release.yml` fetches the three files and their sha256 sums from Loyalsoldier every Thursday (UTC 06:00) and on `workflow_dispatch`. It fails if a checksum does not match. No secrets.

## Credit

Data and formats come from [Loyalsoldier/geoip](https://github.com/Loyalsoldier/geoip), GPL-3.0. This mirror keeps that license.

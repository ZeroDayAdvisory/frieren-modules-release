# frieren-modules-release (ZeroDay Advisory™)

Release/catalog repository for custom modules built for
[**Frieren**](https://github.com/xchwarze/frieren), the micro-framework for
security gadgets on OpenWrt routers/SBCs created by **DSR! (xchwarze)** —
<https://github.com/xchwarze/frieren>. All credit for the Frieren framework
itself belongs to its original author; this repo only packages third-party
modules built on top of it.

This repo is consumed directly by the Frieren panel's **Modules** tab: it
hosts the module index (`json/modules.json`) and the packaged module bundles
(`modules/<name>-<version>.tar.gz`).

Module **source code** lives in the fork:
<https://github.com/ZeroDayAdvisory/frieren> (forked from
[xchwarze/frieren](https://github.com/xchwarze/frieren))

## Use it as your module source

Point your panel at this repo by setting, in `api/config/config.php` on the device:

```php
const MODULE_SERVER_URL = 'https://raw.githubusercontent.com/ZeroDayAdvisory/frieren-modules-release/master';
```

The Modules tab will then list the modules below as installable (download →
checksum‑verify → extract into `/usr/share/frieren/modules`).

## Modules

| Module | Title | What it does |
|--------|-------|--------------|
| `theme` | Theme Customizer | Recolor the whole panel, pick module icon styles/colors, banner/background images |
| `captures` | Captures | Browse per-device honeypot pcap sessions on USB + live honeypot client table |
| `pcapview` | PCAP Analysis | tcpdump BPF filters + ASCII/hex decode over saved captures (no tshark needed) |
| `syshealth` | System Health | Disk / temp / memory / load + daemon status widget |
| `chanmap` | Channel Map | 2.4/5 GHz channel utilization, congestion scoring, frame activity |
| `macfilter` | MAC Allow-List | Manage Aura's shared deauth/MITM allow-list + recon results |
| `hsharvest` | Handshake Harvester | WPA handshake capture workflow |
| `livecap` | Live Capture | Real-time management-frame feed from the monitor radios |
| `probetracker` | Probe Tracker | Track probe requests and the networks devices are looking for |
| `kismet` | Kismet | Bundled Kismet WiFi/Bluetooth sensor with web UI |
| `bettercap` | Bettercap | Network recon/MITM framework (ARP spoofing, sniffing, HTTP/S proxying) |
| `mdk4` | MDK4 | 802.11 denial-of-service / stress-testing toolkit |
| `wireshark` | Wireshark | Remote packet capture gateway via rpcapd |

## Layout

```
json/modules.json                 # catalog index (name, version, size, sha256, …)
modules/<name>-<version>.tar.gz   # packaged bundle; extracts to <name>/
```

Each bundle contains the module's PHP controller/helper, `manifest.json`,
`icon.png`, and the gzip‑encoded `module.umd.js` (served with
`Content-Encoding: gzip`).

## Credit

**Frieren** (the framework these modules extend) was created by **DSR!** —
<xchwarze@gmail.com> — <https://github.com/xchwarze/frieren>. None of the
module authors here are affiliated with or claim authorship of the Frieren
framework itself.

## License

PolyForm Noncommercial License 1.0.0 — see [LICENSE.md](LICENSE.md). Required
notice: Copyright DSR! <xchwarze@gmail.com>. See the source fork for
per-file license headers.

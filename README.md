# frieren-modules-release (ZeroDay Advisory™)

Release/catalog repository for the custom [Frieren](https://github.com/xchwarze/frieren)
modules built by ZeroDay Advisory™. This repo is consumed directly by the
Frieren panel's **Modules** tab: it hosts the module index (`json/modules.json`)
and the packaged module bundles (`modules/<name>-<version>.tar.gz`).

Module **source code** lives in the fork:
<https://github.com/ZeroDayAdvisory/frieren>

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
| `captures` | Captures | Browse per-device honeypot pcap sessions on USB + live honeypot client table |
| `pcapview` | PCAP Analysis | tcpdump BPF filters + ASCII/hex decode over saved captures (no tshark needed) |
| `syshealth` | System Health | Disk / temp / memory / load + daemon status widget |
| `chanmap` | Channel Map | 2.4/5 GHz channel utilization, congestion scoring, frame activity |
| `macfilter` | MAC Allow-List | Manage Aura's shared deauth/MITM allow-list + recon results |
| `hsharvest` | Handshake Harvester | WPA handshake capture workflow |
| `livecap` | Live Capture | Real-time management-frame feed from the monitor radios |
| `probetracker` | Probe Tracker | Track probe requests and the networks devices are looking for |

## Layout

```
json/modules.json                 # catalog index (name, version, size, sha256, …)
modules/<name>-<version>.tar.gz   # packaged bundle; extracts to <name>/
```

Each bundle contains the module's PHP controller/helper, `manifest.json`,
`icon.png`, and the gzip‑encoded `module.umd.js` (served with
`Content-Encoding: gzip`).

## License

Framework and modules follow the upstream Frieren licensing. See the source
fork for per-file license headers.

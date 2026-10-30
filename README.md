# EarthCraft for Craft Unofficial Launcher

**An unofficial mirror** of [EarthCraft](https://github.com/therichronicles/EarthCraft) releases, maintained by
[YalKouassi](https://github.com/YalKouassi), so that
[Craft Unofficial Launcher](https://github.com/YalKouassi/craft-unofficial-launcher) can install
and update EarthCraft.

This repo is **not affiliated with, endorsed by or supported by the EarthCraft contributors** (the authors of EarthCraft),
**or by ArtCraft**. Report problems with EarthCraft itself upstream at
<https://github.com/therichronicles/EarthCraft>; report problems with this mirror here.

## What this repo publishes

The packages in this repo's releases are **EarthCraft's own builds**, as published on
[therichronicles/EarthCraft's releases](https://github.com/therichronicles/EarthCraft/releases). Nothing is rebuilt and no program file is
changed. Each release here:

- downloads upstream's packages and verifies each one before using it;
- renames them to the launcher's `<id>-<version>-<os>-<arch>` naming and, only where the launcher
  couldn't install an archive's layout, repacks that archive (the same files with the same bytes,
  in different folders);
- adds `craft-app.json`, the icon, `SHA256SUMS.txt`, and upstream's licence files from the same tag.

The notes of each release list every file, the upstream asset it came from, its SHA-256, and
whether it was repacked, so you can compare it with upstream's release.

### For EarthCraft

Upstream already names its packages almost the way the launcher expects; they are **renamed**
only where the platform token differs (`linux-x64` becomes `linux-x86_64`, `linux-arm64` becomes
`linux-aarch64`, `freebsd-x64` becomes `freebsd-x86_64`) and otherwise mirrored **byte for byte**.
Every download is checked against upstream's `SHA256SUMS.txt` first.

On Windows this bridge publishes the **MSI** only: upstream's portable `earthcraft.exe` carries no
version resource, which the launcher needs to confirm a portable install.

Not mirrored: the Windows portable zips and setup `.exe`, the snaps, the AppImage `.zsync` files and the macOS self-update zip.

## How it runs

[`.github/workflows/bridge.yml`](.github/workflows/bridge.yml) runs every 3 hours. It uses
[craft-bridge](https://github.com/YalKouassi/craft-bridge) with [`bridge.toml`](bridge.toml) to
check upstream's latest release and mirror it if this repo doesn't have it yet. If upstream starts
publishing its own `craft-app.json`, the bridge stops publishing, and the launcher should point at
upstream directly.

Using this mirror means trusting its maintainer as well as upstream; see
[craft-bridge's Trust section](https://github.com/YalKouassi/craft-bridge#trust).

## Licences

EarthCraft is licensed by its authors under MIT; each release attaches upstream's licence files.
This repo's own files (the config, workflow and this README) are available under MIT OR
Apache-2.0 ([LICENSE-MIT](LICENSE-MIT), [LICENSE-APACHE](LICENSE-APACHE)).

<p align="center"><img src="assets/app-logo-256.png" width="112" alt="Empower Smart Recovery"></p>

# Empower Smart Recovery — Downloads

This repository hosts **downloads and issue tracking** for Empower Smart Recovery, the
recovery companion to [Empower Smart Deploy](https://github.com/mattpetosa/empower-smart-deploy-releases):
a guided Windows app that restores a corrupted Waters **Empower 3** database — or proves
your disaster-recovery plan by restoring backups onto a test server — using Waters' own
documented restore procedure from the Empower 3.8.0–3.10.0 media.

**[⬇ Download the latest release](https://github.com/mattpetosa/empower-smart-recovery-releases/releases/latest)** — or grab it from
[empower.mhpwebserver.com](https://empower.mhpwebserver.com/recovery.html) (self-updating web installer).

## What it does

- **Recover Database** — data-corruption recovery on the same server: restores the
  database to the point of failure from your backup set.
- **DR Restore / Test** — disaster recovery onto a freshly installed or test server;
  running it against a test server *is* your DR script test.
- **Browse-to-restore** — pick the newest control-file backup (`C-…`) and the backup
  folder and database ID are derived automatically; add the Oracle SYS password and go.
- **Live console + progress** — everything RMAN, SQL*Plus and the Waters restore script
  print streams into the app in real time under a phase-tracked progress bar.
- **Pre-flight checks & clear verdicts** — Oracle install, Waters services, keystore
  wallets and database state are verified first; expected Oracle messages are recognised
  and anything unexpected is flagged, with the full restore log preserved.
- **Check System** — a free read-only scan: Empower version, Oracle home, services,
  newest backup found, recovery scripts, disk space.

## Requirements

- Windows 10/11 or Windows Server 2016–2025 (x64), run as Administrator.
- Runs on the Empower **database server** (Oracle 19c database home present).
- A license key — request one at
  [empower.mhpwebserver.com/license.html](https://empower.mhpwebserver.com/license.html)
  (Waters email required; activation itself works offline).

## Issues

Found a problem? [Open an issue](https://github.com/mattpetosa/empower-smart-recovery-releases/issues).
Source code is maintained in a private repository.

# Release history

Newest first. Downloads are on the [Releases](https://github.com/mattpetosa/empower-smart-recovery-releases/releases) page.

## v3.10.0.1-1.4.5 (2026-10-14)

### Changed
- **The header's license chip just says "Licensed".** The full text (who it's licensed to and when it expires) was long enough to crowd the header's other buttons. Click **Licensed** to see who the license is for, when it expires, its license ID and when this computer last checked in, with a button to enter a different key.

## v3.10.0.1-1.4.4 (2026-10-13)

### Changed
- **Built on the shared Smart Tools engine, the same one Empower Smart Deploy uses.** Steps, prompts, activation, updates and run logs now work the same way in both apps.
- **Prompts no longer replace each other.** A second prompt opens on top of the first, and the first one comes back once the second is answered.
- **Cancelling a prompt ends the run as cancelled, and the step says why.** If you cancel "Start restore?", the backup choice or activation, that step shows "Skipped" with the reason (for example "Cancelled before the restore started"), the steps after it show "Not run — cancelled", and the run log records the run as cancelled. A network timeout inside a step now fails that step instead of ending the run as if you had cancelled.
- **Activation.** The activation prompt links to the license page ("Open the license page"); request a key there and choose Recovery. An expired key, a key activated on another computer and a clock problem each get their own explanation, and a key for another Smart Tools app is now explained as such when it doesn't validate.
- **Check for updates keeps checking even when the license can't be confirmed.** The check for a newer version still runs, and you can enter a new key at the end. Its steps are now Activation server, Check for a newer version, Download and Ready.
- **The "update ready" prompt waits until a running task finishes.** It no longer interrupts a run; the Relaunch button at the top offers the update afterwards.
- **Updates are applied by a safer swap.** The new version is renamed into place, and the previous one is put back if that fails. Updates are no longer downloaded into C:\Client\Updates.
- **Roll back:** if a build can't be downloaded or verified, one short message says so.
- **Shorter recovery cards.** Disaster Recovery & Testing and Data Corruption Recovery keep only the key points, so both fit on the home screen without scrolling.
- **The window fits small screens,** such as 1024×768 Remote Desktop sessions. After an update relaunch it is restored and brought to the front.
- **Pressing Start rebuilds the checklist first,** so it reflects the computer as it is at that moment (it used to be prepared only once, when the list was empty).
- **The step list follows the running step.** Scroll up and it stays where you are; it follows again when you scroll back to the bottom or the next step starts.
- **Run logs:** small wording changes in the header lines.

### Added
- **Unexpected errors are written to a crash log:** `C:\Client\Logs\Empower Smart Recovery\ESR_crash_<time>.log`.

### Fixed
- **Database checks no longer write the SYS password to a temporary file.** It is handed straight to SQL*Plus instead.
- **A disaster recovery stops with a clear message when the Fast Recovery Area or archive log location can't be read back from the database** (the database query failed, or part of the path matches the SYS password), **or when one of those folders can't be listed.** Waters requires those folders to be checked before a disaster recovery, so the restore no longer goes ahead without that check. A data corruption recovery warns instead when the Fast Recovery Area can't be read back.
- **A database check now always reports a failure when Oracle refuses the SYS login.**
- **A settings file that can't be read is kept aside instead of being overwritten,** and settings are saved in one step, so an interrupted save can't leave a half-written file.
- **Activating from the top of the window no longer saves a key the licensing server refuses.** (1.3.4 fixed this for the Update & Download license step only.)
- **Single-button notices show one OK button,** instead of two OK buttons side by side.

## v3.10.0.1-1.3.4 (2026-10-11)

### Fixed
- **The SYS password is masked in the restore logs left in C:\Client\DRScripts.** Waters' restore script writes it into its own log there, and C:\Client is a shared folder. It is now masked as soon as the restore finishes, and in logs from earlier restores the next time a restore is staged (when the same SYS password is entered).
- **A license key the licensing server refuses is no longer saved.** It used to replace the previous key and keep working while the computer was offline.
- **The settings folder in ProgramData is now open to administrators only.** It holds the license key; other users on the computer could read it before.
- **Downloads no longer re-check every file each time.** The record of files already verified couldn't be read back, so each sync re-checked the whole download folder.

### Removed
- **Unpacking a Client.zip found next to the app when the server can't be reached.** That came from the old pre-built offline ISO and wasn't signed. The restore scripts this app needs are built into it.

## v3.10.0.1-1.3.3 (2026-10-08)

### Fixed
- **The ring on the running step turns.** Since 1.3.0 it stood still on many computers while a step ran. It now turns once a second for as long as the step runs.
- **The window stays responsive while a step runs.** Each step does its work in the background, so the window can be moved and Cancel answers straight away while a step is busy.

## v3.10.0.1-1.3.0 (2026-10-08)

### Changed
- **A refreshed step list.** Numbered steps, a spinning ring on the step that is running, and a progress bar that fills one segment per step.

## v3.10.0.1-1.2.0 (2026-10-07)

### Changed
- **Downloads now need an activated copy.** Syncing files into C:\Client proves this copy's license to the server for each download session, without sending the license key. An unactivated copy is told to activate before any file is tried. App updates are not affected — every copy still updates itself, and the restore scripts built into the app still work offline.

## v3.10.0.1-1.1.7 (2026-10-06)

### Changed
- **One download, no offline ISO.** The Waters restore scripts are now built into the app, and it puts them in C:\Client\DRScripts the first time it opens — so the single "Download App" file works on a server with no internet. A newer script synced from the server is never overwritten. The separate offline ISO is gone.

## v3.10.0.1-1.1.6 (2026-10-06)

### Changed
- **The app tells the license site it's in use.** When an activated copy opens (at most twice a day), it quietly checks in, so the license holder's activations page shows when each computer last used the app and on which version. It sends a one-way fingerprint of the license key — never the key itself — and does nothing if the computer is offline.
- **Check for app updates from the header.** A small round arrow button beside the version opens a window that shows each step as it happens: the license confirmed with the activation server, the check for a newer version, the download (verified before it's kept), and finally **Restart now** / **Later** — or "You have the latest version". After an update the version in the header reads "Updated to v…" in green for that session.
- **Every copy updates, activated or not** — at startup and from the button. The license still unlocks the app's actions and the C:\Client downloads.

## v3.10.0.1-1.1.5 (2026-10-06)

### Fixed
- **Activation reaches the licensing server again, and the "install complete" email is sent again.** Since the app's code was obfuscated (September), its requests to the licensing server failed inside the app before they were sent: activation quietly fell back to offline activation, and the email the license holder gets when an Empower install finishes was never sent. Both work again.

## v3.10.0.1-1.1.4 (2026-10-06)

### Changed
- **Logs go into a folder named for this app:** `C:\Client\Logs\Empower Smart Recovery`, so each Smart Tools app's logs are kept apart. The folder can be read by administrators only (C:\Client is shared on the network). Logs this app wrote straight into `C:\Client\Logs` before are moved there the first time it opens.

# TN Tray 1.0.1

Compatibility and reliability update. Adds support for Thunderbird 154 and fixes a stale update-manifest hash left over from the 1.0.0 release.

## Download

Download the attached XPI file:

- `tn-tray-1.0.1.xpi`

## SHA256

```
ae0528b0f63724ca5b57ef59bf47cdd837c296aac50dc90bb85c80bda18ec58d
```

## Compatibility

- Thunderbird 152.* through 154.* (Windows only).

## What's new

- **Thunderbird 154 support.** `strict_max_version` raised to `154.*`.
- **Coexistence with Thunderbird 154's native close-to-tray.** When TN Tray's own tray icon is enabled (the default), it now also backs up and disables the new native `mail.closeToTray` and `mail.closeToTray.startInTray` preferences on Thunderbird 154+, the same way it already handled the legacy tray icon preferences — so the native feature and TN Tray don't both react to the same window-close event. Original values are restored automatically on real uninstall or disable. This only touches those preferences on Thunderbird 154 and later, where they actually exist.
- **Fixed a stale hash in the update manifest.** `docs/updates.json`, hosted on GitHub Pages for automatic updates, had a SHA-256 for the 1.0.0 entry that didn't match the actual published `.xpi`. Anyone relying on Thunderbird's automatic update check against that manifest would have failed hash verification. Corrected in this release.
- Updated README, FAQ, and the "use only this extension's tray icon" option's description (English and Portuguese) to describe the actual coexistence behavior with Thunderbird 154's native tray feature now that it has shipped.

## Installation

1. Download `tn-tray-1.0.1.xpi` from this release.
2. Open Thunderbird.
3. Go to **Add-ons and Themes**.
4. Click the gear icon.
5. Choose **Install Add-on From File…**.
6. Select the downloaded XPI file.
7. Confirm the installation.
8. Restart Thunderbird if requested.

Existing 1.0.0 installations will pick this up automatically through Thunderbird's add-on update mechanism using the extension's self-hosted update manifest.

## Notes

TN Tray uses Thunderbird Experiment APIs because the custom tray icon, its context menu, and the Windows auto-start registry entry are not exposed through standard WebExtension APIs.

addons.thunderbird.net is currently not accepting new add-ons using Experiment APIs unless they use unmodified copies of published Thunderbird API drafts. Distribution is handled through GitHub Releases while that restriction remains in place.

This repository is used for public releases, documentation, support, issues, and discussions.

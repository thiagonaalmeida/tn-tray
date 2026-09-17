# TN Tray 1.0.3

Compatibility update. Adds support for Thunderbird 156.

## Download

Download the attached XPI file:

- `tn-tray-1.0.3.xpi`

## SHA256

```
7632be5d15cade3f803eedfd57a0b0a19b6974feb10b25a338f040cd6a1f36fd
```

## Compatibility

- Thunderbird 152.* through 156.* (Windows only).

## What's new

- **Thunderbird 156 support.** `strict_max_version` raised to `156.*`.
- **No code changes needed.** A source-level review of the Thunderbird 156.0 release confirmed nothing relevant to TN Tray changed: `mail/base/content/closeToTray.mjs`, the `-MapiStartup`/`-url` launch-flag handling in `MessengerContentHandler.sys.mjs`, and the Windows-specific preference list in `MailGlue.sys.mjs` (`mail.biff.show_tray_icon`, `mail.closeToTray`, `mail.closeToTray.startInTray`) are all unchanged from 154/155. The 156.0 release notes mention a fix for Thunderbird's own native tray icon (Enter key not restoring the window), but that's Thunderbird's own tray icon, which TN Tray suppresses in favor of its own — it doesn't affect TN Tray. This release is a compatibility bump only.

## Installation

1. Download `tn-tray-1.0.3.xpi` from this release.
2. Open Thunderbird.
3. Go to **Add-ons and Themes**.
4. Click the gear icon.
5. Choose **Install Add-on From File…**.
6. Select the downloaded XPI file.
7. Confirm the installation.
8. Restart Thunderbird if requested.

Existing installations will pick this up automatically through Thunderbird's add-on update mechanism using the extension's self-hosted update manifest. If Thunderbird already auto-updated to 156 and disabled TN Tray as incompatible, this release re-enables it once installed.

## Notes

TN Tray uses Thunderbird Experiment APIs because the custom tray icon, its context menu, and the Windows auto-start registry entry are not exposed through standard WebExtension APIs.

addons.thunderbird.net is currently not accepting new add-ons using Experiment APIs unless they use unmodified copies of published Thunderbird API drafts. Distribution is handled through GitHub Releases while that restriction remains in place.

This repository is used for public releases, documentation, support, issues, and discussions.

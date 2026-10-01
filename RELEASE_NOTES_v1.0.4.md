# TN Tray 1.0.4

Compatibility update. Adds support for Thunderbird 157.

## Download

Download the attached XPI file:

- `tn-tray-1.0.4.xpi`

## SHA256

```
f9bbab28854d415611c3868a0a456f1cecf3e8a75f668e3a9cd6988956e52fc9
```

## Compatibility

- Thunderbird 152.* through 157.* (Windows only).

## What's new

- **Thunderbird 157 support.** `strict_max_version` raised to `157.*`.
- **No code changes needed.** A source-level review of the Thunderbird 157.0 release confirmed nothing relevant to TN Tray changed: `mail/base/content/closeToTray.mjs` and the Windows-specific preference list in `MailGlue.sys.mjs` (`mail.biff.show_tray_icon`, `mail.closeToTray`, `mail.closeToTray.startInTray`) are unchanged. `MessengerContentHandler.sys.mjs` gained a new `#handleFelt()` call at the start of command-line handling, but it's a no-op outside enterprise-only Firefox builds, and the `-MapiStartup`/`-url` flag handling TN Tray's boot detection depends on is unchanged. This release is a compatibility bump only.

## Installation

1. Download `tn-tray-1.0.4.xpi` from this release.
2. Open Thunderbird.
3. Go to **Add-ons and Themes**.
4. Click the gear icon.
5. Choose **Install Add-on From File…**.
6. Select the downloaded XPI file.
7. Confirm the installation.
8. Restart Thunderbird if requested.

Existing installations will pick this up automatically through Thunderbird's add-on update mechanism using the extension's self-hosted update manifest. If Thunderbird already auto-updated to 157 and disabled TN Tray as incompatible, this release re-enables it once installed.

## Notes

TN Tray uses Thunderbird Experiment APIs because the custom tray icon, its context menu, and the Windows auto-start registry entry are not exposed through standard WebExtension APIs.

addons.thunderbird.net is currently not accepting new add-ons using Experiment APIs unless they use unmodified copies of published Thunderbird API drafts. Distribution is handled through GitHub Releases while that restriction remains in place.

This repository is used for public releases, documentation, support, issues, and discussions.

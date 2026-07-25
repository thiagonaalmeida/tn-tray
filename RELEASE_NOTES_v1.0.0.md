# TN Tray 1.0.0

Initial public release of **TN Tray**, a Thunderbird extension for Windows that gives full control over minimize/close-to-tray behavior, with a custom tray icon, unread badge, and its own right-click menu.

## Download

Download the attached XPI file:

- `tn-tray-1.0.0.xpi`

## SHA256

```
50d3df9c29dee15fb3784850aafafd90bdc124709c0df97313af8b9207cd3e46
```

## Compatibility

- Thunderbird 152.* and 153.* (Windows only).

## Highlights

- Close to tray via the window's X button, with a fully custom Win32 tray icon and context menu (Restore / Compose new message / Check for new messages / Exit).
- Silent start in tray when launched via Windows Startup, detected through the real process command line — manual launches always open normally.
- Unread count badge on the tray icon, using Thunderbird's own new-mail icon.
- Click detection runs on a dedicated `ChromeWorker` thread, immune to main-thread jank during busy boot.
- Automatic recovery if `explorer.exe` restarts and the notification area is wiped out from under the extension.
- Auto-start with Windows managed via the registry `Run` key, added/removed automatically on enable/disable/uninstall.
- Suppresses Thunderbird's native tray icon (which only ever exposes "Exit") in favor of this extension's own, restoring the original preference values on uninstall.
- Full localization (English default, Portuguese) for the settings page, tray menu, and unread-count tooltip, matching Thunderbird's own UI language.
- Diagnostic logging, off by default, with a "Show log file" button to open its location directly in Explorer.

## Installation

1. Download `tn-tray-1.0.0.xpi` from this release.
2. Open Thunderbird.
3. Go to **Add-ons and Themes**.
4. Click the gear icon.
5. Choose **Install Add-on From File…**.
6. Select the downloaded XPI file.
7. Confirm the installation.
8. Restart Thunderbird if requested.

After installing this version, future releases can be discovered through Thunderbird's add-on update mechanism using the extension's self-hosted update manifest.

## Notes

TN Tray uses Thunderbird Experiment APIs because the custom tray icon, its context menu, and the Windows auto-start registry entry are not exposed through standard WebExtension APIs.

addons.thunderbird.net is currently not accepting new add-ons using Experiment APIs unless they use unmodified copies of published Thunderbird API drafts. Distribution is handled through GitHub Releases while that restriction remains in place.

This repository is used for public releases, documentation, support, issues, and discussions.

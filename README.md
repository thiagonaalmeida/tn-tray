# TN Tray

**TN Tray** is a Thunderbird extension for Windows that gives you full control over minimize/close-to-tray behavior, with a custom tray icon, unread badge, and its own right-click menu — something Thunderbird's native tray integration has never fully provided.

There are other tray extensions for Thunderbird out there, but none of them quite matched what felt missing, or worked the way it seemed like they should. TN Tray is an independent take on the problem, built from scratch.
> This repository hosts public releases, documentation, support, issues, and discussions. The extension is distributed as a packaged `.xpi` file through GitHub Releases.

## Features

- Close to tray: clicking the window's X sends Thunderbird to the system tray instead of quitting.
- Silent start in tray when launched from Windows Startup, without the window flashing on screen first. Launching manually (Start menu, desktop shortcut, double-click) still opens normally.
- Custom tray icon and menu, built directly on the Win32 API (`Shell_NotifyIcon`), with Restore / Compose new message / Check for new messages / Exit.
- Unread badge on the tray icon, mirroring Thunderbird's own new-mail icon.
- Auto-start with Windows, managed through the registry `Run` key (no shortcut needed).
- Self-healing: automatically detects and recovers if `explorer.exe` restarts and wipes the notification area.
- Includes English and Portuguese localization for the settings page, tray menu, and unread-count tooltip, matching Thunderbird's own UI language.

## Compatibility

- Thunderbird **152.*** and **153.***.
- Windows only.

## Known limitations

- TN Tray currently manages the main Thunderbird window opened at startup. Additional 3-pane windows opened during the same session aren't independently managed by the close-to-tray behavior.
- Windows auto-start uses a single registry entry per Windows user. Multiple Thunderbird installations or profiles under the same user may overwrite each other's entry — disabling Windows auto-start, or disabling TN Tray, in one profile can also remove the shared entry that another profile or installation relies on.

## Why not just use Thunderbird's built-in tray support?

Thunderbird has long had a legacy `mail.minimizeToTray` preference, and starting with **Thunderbird 154** it gains a proper native "close to tray" / "start in tray" feature. TN Tray has already been reviewed in detail against that implementation, and full compatibility is the top priority for the next release. The current 1.0.0 release officially supports Thunderbird 152 and 153.

## Installation

1. Download the latest `.xpi` file from the [Releases](../../releases) page.
2. Open Thunderbird.
3. Go to **Add-ons and Themes**.
4. Click the gear icon.
5. Choose **Install Add-on From File…**.
6. Select the downloaded XPI file.
7. Confirm the installation.
8. Restart Thunderbird if needed.

Thunderbird does not require add-on signing (`xpinstall.signatures.required` is `false` by default), so the downloaded `.xpi` installs directly without any warning to bypass. Manually installed releases include a self-hosted update manifest, so future releases can be discovered through Thunderbird's own add-on update mechanism.

## Thunderbird Add-ons status

TN Tray uses privileged [WebExtension Experiment APIs](https://developer.thunderbird.net/add-ons/mailextensions/experiments) because the custom tray icon, its context menu, and the Windows auto-start registry entry are not exposed through standard WebExtension APIs.

addons.thunderbird.net is currently not accepting new add-ons using Experiment APIs unless they use unmodified copies of published Thunderbird API drafts. Distribution is handled through GitHub Releases while that restriction remains in place.

## Options

Open the extension's preferences (Add-ons and Themes → TN Tray → Preferences) to control:

- Use only this extension's tray icon (suppresses Thunderbird's native one)
- Start Thunderbird with Windows
- Start minimized in the tray on boot
- Enable diagnostic logging (writes to `%TEMP%\tntray-debug.log`, off by default), with a "Show log file" button to open its location directly in Explorer

### Default settings

- Use only TN Tray's tray icon: **enabled**
- Start Thunderbird with Windows: **enabled**
- Start minimized in the tray on boot: **enabled**
- Diagnostic logging: **disabled**

Installing TN Tray immediately suppresses Thunderbird's native tray icon and adds an entry to the Windows `Run` registry key for the current user — both can be turned off in Preferences right after installing, if that's not what you want.

## Privacy

TN Tray collects no data and its own code makes no network requests. The one exception is Thunderbird's standard add-on update check, which periodically contacts the extension's self-hosted update manifest on GitHub Pages — the same mechanism any self-hosted add-on uses, with no tracking or identifiers added by TN Tray. Diagnostic logging, when explicitly enabled by the user, only writes to a local temp file for troubleshooting and is never transmitted anywhere. See [PRIVACY.md](PRIVACY.md) for details.

## Technical overview

| File | Purpose |
|---|---|
| `background.js` | WebExtension orchestration: wires up options, unread counting, menu commands |
| `experiments/trayIcon/` | Privileged API: tray icon/menu via `Shell_NotifyIconW`, window hide/show/transparency, close-to-tray hijack |
| `experiments/trayIcon/poll-worker.js` | `ChromeWorker` thread that polls for tray icon clicks/hover, avoiding native window-procedure callbacks |
| `experiments/launchMode/` | Detects the `-trayboot` launch flag and manages the Windows `Run` registry auto-start entry |
| `options/` | Settings UI |

## Support

Use [Issues](../../issues) for bug reports and [Discussions](../../discussions) for questions, feedback, and feature ideas. See [SUPPORT.md](SUPPORT.md) for what to include in a bug report.

## Sponsorship

If this extension helps your Thunderbird workflow, GitHub Sponsors support is welcome.

## License

[Mozilla Public License 2.0](LICENSE).

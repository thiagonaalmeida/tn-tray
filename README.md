# TN Tray

**TN Tray** is a Thunderbird extension for Windows with close-to-tray and start-in-tray behavior, a custom tray icon, an optional numeric count, and a right-click menu.

> This repository hosts public releases, documentation, support, issues, and discussions. The extension is distributed as a packaged `.xpi` file through GitHub Releases.

## Features

- Close to tray: clicking the window's X sends Thunderbird to the system tray instead of quitting.
- Silent start in tray when launched from Windows Startup, without the window flashing on screen first. Launching manually (Start menu, desktop shortcut, double-click) still opens normally.
- Custom tray icon and menu, built directly on the Win32 API (`Shell_NotifyIcon`), with Restore / Compose new message / Check for new messages / Exit.
- Dot indicator for new mail, with an optional numeric tray badge (off by default) using the same count as Thunderbird's taskbar badge.
- Choose new-message or unread-message counting through Thunderbird's profile setting; the choice also affects its taskbar badge and requires a restart.
- Auto-start with Windows, managed through the registry `Run` key (no shortcut needed).
- Self-healing: automatically detects and recovers if `explorer.exe` restarts and wipes the notification area.
- Includes English and Portuguese localization for the settings page, tray menu, and unread-count tooltip, matching Thunderbird's own UI language.

## Compatibility

- Thunderbird **152.*** through **162.***.
- Windows only.
- Source review and runtime checks used Thunderbird **161.0b4**. The 162 ceiling is a compatibility allowance; 162 has not been tested.

## Known limitations

- TN Tray currently manages the main Thunderbird window opened at startup. Additional 3-pane windows opened during the same session aren't independently managed by the close-to-tray behavior.
- Windows auto-start uses a single registry entry per Windows user. Automatic startup handling preserves an entry belonging to another Thunderbird executable. Explicitly changing the startup option can replace or remove that shared entry; profiles using the same executable still share it.

## Thunderbird's native tray settings

On Thunderbird 154+, enabling **Use only this extension's tray icon** (the default) backs up and disables the native close-to-tray/start-in-tray preferences so both handlers do not process the same close event. You can turn the option off in Preferences to use the native behavior alongside TN Tray. The backed-up preferences are restored when the extension is disabled or uninstalled.

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
- Show count on the tray icon (off by default; otherwise a dot is used)
- Thunderbird count type: New messages or Unread messages (a profile setting shared with the taskbar badge; restart after changing)
- Start Thunderbird with Windows
- Start minimized in the tray on boot
- Enable diagnostic logging (writes to `%TEMP%\tntray-debug.log`, off by default), with a "Show log file" button to open its location directly in Explorer

### Default settings

- Use only TN Tray's tray icon: **enabled**
- Start Thunderbird with Windows: **enabled**
- Start minimized in the tray on boot: **enabled**
- Numeric tray count: **disabled**
- Count type: follows the current Thunderbird profile setting
- Diagnostic logging: **disabled**

Installing TN Tray suppresses Thunderbird's native tray icon and enables Windows startup by default. Automatic startup handling preserves an existing entry for another Thunderbird executable. You can change these options in Preferences.

High counts (10, 99, 99+) were checked in images at the tray's actual size. If the number is difficult to read, please [open an issue](../../issues).

## Privacy

TN Tray collects no data and its own code makes no network requests. The one exception is Thunderbird's standard add-on update check, which periodically contacts the extension's self-hosted update manifest on GitHub Pages — the same mechanism any self-hosted add-on uses, with no tracking or identifiers added by TN Tray. Diagnostic logging, when explicitly enabled by the user, only writes to a local temp file for troubleshooting and is never transmitted anywhere. See [PRIVACY.md](PRIVACY.md) for details.

## Technical overview

| File | Purpose |
|---|---|
| `background.js` | WebExtension orchestration: wires up options, unread counting, menu commands |
| `experiments/trayIcon/` | Privileged API: tray icon/menu via `Shell_NotifyIconW`, window hide/show/transparency, close-to-tray hijack |
| `experiments/trayIcon/poll-worker.js` | `ChromeWorker` thread that polls for tray icon clicks/hover, avoiding native window-procedure callbacks |
| `experiments/launchMode/` | Detects the `-MapiStartup -url` launch flags and manages the Windows `Run` registry auto-start entry |
| `options/` | Settings UI |

## Support

Use [Issues](../../issues) for bug reports and [Discussions](../../discussions) for questions, feedback, and feature ideas. See [SUPPORT.md](SUPPORT.md) for what to include in a bug report.

## Sponsorship

If this extension helps your Thunderbird workflow, GitHub Sponsors support is welcome.

## License

[Mozilla Public License 2.0](LICENSE).

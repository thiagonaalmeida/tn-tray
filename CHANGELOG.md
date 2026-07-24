# Changelog

## 1.0.0

First public release.

- Close to tray via the window's X button, with a fully custom Win32 tray icon and context menu (Restore / Compose new message / Check for new messages / Exit).
- Silent start in tray when launched via Windows Startup (`-trayboot` flag), detected through the real process command line — manual launches always open normally.
- Native window transparency trick during boot to avoid the visible window flash, while still waiting for Thunderbird's own `delayedStartupPromise` so new-mail checking and notifications keep working correctly.
- Unread count badge on the tray icon, using Thunderbird's own `newmail.ico`.
- Click detection runs on a dedicated `ChromeWorker` thread, immune to main-thread jank during busy boot.
- Automatic recovery if `explorer.exe` restarts and the notification area is wiped out from under the extension.
- `window.focus()` interception to fix a white-flash bug when Thunderbird is reactivated externally (e.g. clicking a pinned taskbar icon) while hidden.
- Auto-start with Windows managed via the registry `Run` key, added/removed automatically on enable/disable/uninstall (with an upgrade-safe guard so a version update doesn't wrongly undo it).
- Suppresses Thunderbird's native tray icon (which only ever exposes "Exit") in favor of this extension's own, restoring the original preference values on uninstall.
- Settings page: use own tray icon, auto-start with Windows, start minimized on boot, diagnostic logging toggle.
- "Check for new messages" added to the tray menu, using Thunderbird's own `MsgGetMessagesForAllAuthenticatedAccounts()` (same as File > Get New Messages).
- Full localization (English default, Portuguese) for the settings page, tray menu, and unread-count tooltip, matching Thunderbird's own UI language.
- Tray menu is now anchored to the actual icon position (via `Shell_NotifyIconGetRect` + `TPM_LEFTALIGN`/`TPM_BOTTOMALIGN`) instead of only the cursor position, so it opens directly above the icon, left-aligned to it, instead of overlapping the Windows 11 hidden-icons flyout. Also trimmed to its natural width (`MNS_NOCHECK`) instead of stretching to the longest label.
- "Show log file" button in settings, next to diagnostic logging, opens the log file location directly in Explorer — no need to type `%TEMP%` manually when sending it for support.
- Pauses the background polling thread while the tray context menu is being shown, and resumes it right after. Real-world logs showed the polling thread's own `Shell_NotifyIconGetRect` calls, running concurrently with the main thread's during `TrackPopupMenu`, correlated with the menu occasionally failing to appear (~12% of right-clicks in test logs) — this removes that concurrent access window.

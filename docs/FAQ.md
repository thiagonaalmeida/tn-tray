# FAQ

## What does TN Tray do?

It adds a custom system tray icon for Thunderbird on Windows, with close-to-tray, start-in-tray on boot, a full right-click menu (Restore, Compose, Check for new messages, Exit), and an unread-count badge.

## Which Thunderbird version is supported?

Thunderbird 152.* and 153.*. Windows only.

## Does it replace Thunderbird's native tray icon?

Yes, by default. TN Tray suppresses Thunderbird's native tray icon (which only ever exposes "Exit") and uses only its own. You can disable this in Preferences if you'd rather have both icons coexist.

## Does it conflict with Thunderbird 154's native close-to-tray feature?

No conflict is expected. TN Tray has already been reviewed in detail against Thunderbird 154's implementation, and full compatibility is the top priority for the next release — the current 1.0.0 release officially supports Thunderbird 152 and 153. TN Tray is designed to keep offering its own custom tray icon, full right-click menu, and unread badge alongside the native feature.

## Why is it distributed on GitHub instead of addons.thunderbird.net?

addons.thunderbird.net is currently not accepting new add-ons that use Experiment APIs unless they use unmodified copies of published Thunderbird API drafts. TN Tray needs Experiment APIs for its custom tray icon, menu, and Windows auto-start integration, so it is distributed through GitHub Releases while that restriction remains in place.

## Does TN Tray collect any data?

No. TN Tray's own code makes no network requests. The one exception is Thunderbird's standard add-on update check, which periodically contacts the extension's self-hosted update manifest on GitHub Pages — the same mechanism any self-hosted add-on uses. Diagnostic logging, when explicitly enabled, only writes to a local temp file. See [PRIVACY.md](../PRIVACY.md) for details.

## Where should I report problems?

Use [Issues](https://github.com/thiagonaalmeida/tn-tray/issues) for reproducible bugs and [Discussions](https://github.com/thiagonaalmeida/tn-tray/discussions) for questions, feedback, and compatibility reports.

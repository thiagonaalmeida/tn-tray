# FAQ

## What does TN Tray do?

It adds a custom system tray icon for Thunderbird on Windows, with close-to-tray, start-in-tray on boot, a full right-click menu (Restore, Compose, Check for new messages, Exit), and an unread-count badge.

## Which Thunderbird version is supported?

Thunderbird 152.* and 153.*. Windows only.

## Does it replace Thunderbird's native tray icon?

Not by default — both can coexist. An option in Preferences lets you suppress Thunderbird's native tray icon and use only TN Tray's.

## Does it conflict with Thunderbird 154's native close-to-tray feature?

No. TN Tray has already been reviewed against Thunderbird 154's implementation and is designed to remain fully compatible with it, continuing to offer its own custom tray icon, full right-click menu, and unread badge alongside the native feature.

## Why is it distributed on GitHub instead of addons.thunderbird.net?

addons.thunderbird.net is currently not accepting new add-ons that use Experiment APIs unless they use unmodified copies of published Thunderbird API drafts. TN Tray needs Experiment APIs for its custom tray icon, menu, and Windows auto-start integration, so it is distributed through GitHub Releases while that restriction remains in place.

## Does TN Tray collect any data?

No. It makes no network requests and sends nothing outside your machine. Diagnostic logging, when explicitly enabled, only writes to a local temp file. See [PRIVACY.md](../PRIVACY.md) for details.

## Where should I report problems?

Use [Issues](https://github.com/thiagonaalmeida/tn-tray/issues) for reproducible bugs and [Discussions](https://github.com/thiagonaalmeida/tn-tray/discussions) for questions, feedback, and compatibility reports.

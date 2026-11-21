# FAQ

## What does TN Tray do?

It adds a custom system tray icon for Thunderbird on Windows, with close-to-tray, start-in-tray on boot, a full right-click menu (Restore, Compose, Check for new messages, Exit), a dot indicator, and an optional numeric count (off by default).

## Which Thunderbird version is supported?

Thunderbird 152.* through 162.*. Windows only.

## Does it replace Thunderbird's native tray icon?

Yes, by default. TN Tray suppresses Thunderbird's native tray icon and uses its own. You can disable this in Preferences to have both icons coexist.

## Does it conflict with Thunderbird 154's native close-to-tray feature?

TN Tray backs up and disables Thunderbird's native `mail.closeToTray` / `mail.closeToTray.startInTray` preferences on 154+ while **Use only this extension's tray icon** is enabled, so both handlers do not process the same close event. You can turn this option off in Preferences to use the native behavior alongside TN Tray.

## How do I show a number on the tray icon?

Enable **Show count on the tray icon** in Preferences. It is off by default and uses the same count as Thunderbird's taskbar badge. Turning it off returns to the dot indicator.

## What is the difference between New messages and Unread messages?

The **Thunderbird count type** choice changes Thunderbird's own `mail.biff.use_new_count_in_badge` preference for this profile. It also affects Thunderbird's taskbar badge, even when TN Tray's numeric badge is off. Restart Thunderbird after changing it so the total initializes correctly.

**New messages** can reset when the new-mail notification is cleared, even if unread messages remain. **Unread messages** decreases when an unread message is read, marked as read, or deleted, within the folders Thunderbird includes in its count. TN Tray uses Thunderbird's count rather than maintaining a separate total.

High counts (10, 99, 99+) were checked in images at the tray's actual size. If you find the number difficult to read, please open an issue.

## Can Windows startup affect another Thunderbird installation?

The Windows Run entry is shared by the current Windows user. Automatic handling preserves an entry for another Thunderbird executable. Explicitly changing **Start Thunderbird with Windows** can replace or remove it. Profiles using the same executable still share the entry.

## Why is it distributed on GitHub instead of addons.thunderbird.net?

addons.thunderbird.net is currently not accepting new add-ons that use Experiment APIs unless they use unmodified copies of published Thunderbird API drafts. TN Tray needs Experiment APIs for its custom tray icon, menu, and Windows auto-start integration, so it is distributed through GitHub Releases while that restriction remains in place.

## Does TN Tray collect any data?

No. TN Tray's own code makes no network requests. The one exception is Thunderbird's standard add-on update check, which periodically contacts the extension's self-hosted update manifest on GitHub Pages — the same mechanism any self-hosted add-on uses. Diagnostic logging, when explicitly enabled, only writes to a local temp file. See [PRIVACY.md](../PRIVACY.md) for details.

## Where should I report problems?

Use [Issues](https://github.com/thiagonaalmeida/tn-tray/issues) for reproducible bugs and [Discussions](https://github.com/thiagonaalmeida/tn-tray/discussions) for questions, feedback, and compatibility reports.

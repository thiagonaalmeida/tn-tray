# Third-Party Notices

TN Tray does not bundle third-party libraries, frameworks, or dependencies.

## Thunderbird badge drawing (MPL-2.0)

The numeric tray badge drawing in `experiments/trayIcon/implementation.js` is adapted from Thunderbird's [SystemTrayBadgeManager](https://github.com/thunderbird/thunderbird-desktop/blob/THUNDERBIRD_161_0b4_RELEASE/mailnews/base/src/SystemTrayBadgeManager.sys.mjs), licensed under the [Mozilla Public License 2.0](LICENSE).

Original badge work: Copyright (c) 2013-2020 Brandon Streiff. The source file retains the MPL-2.0 notice and this credit.

## Native Windows APIs

TN Tray calls native Windows APIs (Win32/Shell32/User32/Advapi32) directly through Thunderbird's `ctypes` mechanism. These are operating system APIs, not bundled third-party code.

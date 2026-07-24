# Privacy Policy — TN Tray

TN Tray does not collect, store, or transmit any personal data, usage data, or telemetry of any kind. It does not make network requests.

The extension reads only what it needs to operate locally on your computer:

- The list of your mail accounts and folders' unread counts (via Thunderbird's own `accounts` and `folders` WebExtension APIs), used exclusively to show an unread-count badge on the system tray icon. This data never leaves your device.
- The Windows command line used to launch Thunderbird (via the Win32 API), used exclusively to detect whether Thunderbird was started automatically with Windows, so the extension can decide whether to start minimized in the tray.

Optional diagnostic logging, disabled by default, can be turned on by the user in the extension's settings. When enabled, it writes plain-text log lines to a local file (`%TEMP%\tntray-debug.log`) on the user's own machine, for troubleshooting purposes only. This file is never sent anywhere by the extension; sharing it (e.g. for support) is entirely up to the user.

No cookies are used. No third-party libraries or services are included. No data is sold, shared, or used for advertising.

Contact: TNCode (via the extension's GitHub repository).

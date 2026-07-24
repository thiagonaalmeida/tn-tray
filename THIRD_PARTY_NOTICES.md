# Third-Party Notices

TN Tray does not bundle any third-party libraries, frameworks, or dependencies. All code (background script, options page, and Experiment API implementations) is original and written specifically for this extension.

TN Tray calls native Windows APIs (Win32/Shell32/User32/Advapi32) directly through Thunderbird's `ctypes` mechanism. These are operating system APIs, not bundled third-party code.

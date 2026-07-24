# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability in TN Tray, please report it privately by opening a [GitHub Issue](https://github.com/thiagonaalmeida/tn-tray/issues) marked as a security concern, or by contacting the maintainer directly rather than disclosing it publicly first.

Please include:

- A description of the vulnerability and its potential impact.
- Steps to reproduce it.
- The Thunderbird version and Windows version you tested on.

## Scope

TN Tray uses privileged WebExtension Experiment APIs to interact with the Win32 API directly (system tray icon, window visibility, registry auto-start entry). Because of this elevated access, security issues in this extension are taken seriously and will be addressed as a priority.

## Supported Versions

Only the latest released version of TN Tray is supported with security fixes.

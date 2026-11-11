# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability in TN Tray, please report it privately through GitHub: open the repository's **Security** tab and click **Report a vulnerability** ([direct link](https://github.com/thiagonaalmeida/tn-tray/security/advisories/new)). Only the maintainer can see the report.

Please do not open a public Issue for security vulnerabilities, and do not disclose them publicly before a fix is available.

Please include:

- A description of the vulnerability and its potential impact.
- Steps to reproduce it.
- The Thunderbird version and Windows version you tested on.

## Scope

TN Tray uses privileged WebExtension Experiment APIs to interact with the Win32 API directly (system tray icon, window visibility, registry auto-start entry). Because of this elevated access, security issues in this extension are taken seriously and will be addressed as a priority.

## Supported Versions

Only the latest released version of TN Tray is supported with security fixes.

# Installing TN Tray

1. Download the latest `.xpi` file from the [Releases](https://github.com/thiagonaalmeida/tn-tray/releases) page.
2. Open Thunderbird.
3. Go to **Add-ons and Themes**.
4. Click the gear icon.
5. Choose **Install Add-on From File…**.
6. Select the downloaded `.xpi` file.
7. Confirm the installation.
8. Restart Thunderbird if needed.

Thunderbird does not require add-on signing (`xpinstall.signatures.required` is `false` by default), so the downloaded `.xpi` installs directly without any warning to bypass.

Manually installed releases include a self-hosted update manifest, so future releases can be discovered through Thunderbird's own add-on update mechanism.

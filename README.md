# BVOS Desktop — releases

Linux releases of **BVOS Desktop** (Blue View OS), the consent-infrastructure desktop app:
an AppImage, a `.deb`, the minisign-signed updater artifact (`.AppImage.sig`) and the updater
manifest (`latest.json`).

The app's built-in updater reads
`https://github.com/Blue-View-Inc/bvos-desktop-releases/releases/latest/download/latest.json`,
downloads the AppImage it names and **verifies it against the public key baked into the app**
before installing. An artifact signed with any other key installs nothing.

What the signature means, and what it does not (stated exactly as the app's About panel does):

- the updater key proves an update **came from us** — it is a minisign (Ed25519) keypair;
- it does **not** make the installer OS-code-signed. On Linux there is no such authority; on
  macOS/Windows a commercial certificate would be a separate, later item.

Artifacts are produced by the `Desktop` GitHub workflow of the source repo (the `bundle` job,
dispatch-only) and published here by hand. The source repository is private.

# Auto-Updates

Kite checks for updates automatically and installs them with one click.

---

## How it works

1. On launch (and every 30 minutes), Kite checks the [latest release](https://github.com/velm-in/kite/releases/latest) for a new version
2. If an update is available, a badge appears in the status bar: **"v0.2.0 available"**
3. Click the badge to download and install
4. Kite restarts with the new version

---

## Signed releases

Every release binary is signed with a private key during the CI build process. When Kite downloads an update, it verifies the signature against the embedded public key before installing.

If the signature doesn't match, the update is rejected. This prevents tampered binaries from being installed.

---

## Update endpoints

Kite checks this URL for update metadata:

```
https://github.com/velm-in/kite/releases/latest/download/latest.json
```

The `latest.json` file is generated automatically by the release CI workflow and contains:
- Version number
- Download URLs for each platform
- Signatures for each binary

---

## Manual download

If auto-update fails or you prefer manual installation, download the latest release directly from the [releases page](https://github.com/velm-in/kite/releases/latest).

---

## Disabling auto-updates

Auto-update checks can be disabled in Settings. The app will still work — you just won't be notified of new versions.

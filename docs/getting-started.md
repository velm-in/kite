# Getting Started

Get from zero to inspecting your first webhook in under 60 seconds.

---

## Install

Download the latest release for your platform from the [releases page](https://github.com/kitebyvelm/kite/releases/latest).

| Platform | File |
|----------|------|
| macOS (Apple Silicon) | `Kite_x.x.x_aarch64.dmg` |
| macOS (Intel) | `Kite_x.x.x_x64.dmg` |
| Windows | `Kite_x.x.x_x64-setup.exe` or `.msi` |
| Linux | `.AppImage` or `.deb` |

**macOS:** Drag Kite to Applications. On first launch, right-click > Open if Gatekeeper blocks it.

**Windows:** Run the installer. Windows Defender SmartScreen may warn — click "More info" > "Run anyway".

**Linux:** Make the AppImage executable (`chmod +x Kite_*.AppImage`) and run it. Or install the `.deb` with `sudo dpkg -i Kite_*.deb`.

---

## No account required

Kite works fully offline for local features. You can send API requests, manage collections, use SSH — all without creating an account.

An account is only needed for:
- Cloud webhook endpoints (receiving webhooks from external services)
- Localhost tunneling
- Cloud sync (Pro/Team)
- Health monitoring & alerts

---

## Your first webhook endpoint

1. Open Kite
2. Click **Webhooks** in the sidebar (or press `Cmd+3`)
3. Click **Create Endpoint**
4. Copy your webhook URL — it looks like `https://kite.velm.in/wh/k7x9m2p1`
5. Paste it into your service (Stripe, GitHub, Twilio, etc.)
6. Trigger an event — the webhook appears in Kite in real time

---

## Your first API request

1. Open a new tab (`Cmd+T`)
2. Type a URL in the address bar (e.g., `https://jsonplaceholder.typicode.com/posts/1`)
3. Select the HTTP method (GET, POST, PUT, etc.)
4. Click **Send** (or press `Cmd+Enter`)
5. Response appears in the bottom panel with status, time, and size

---

## Forward webhooks to localhost

1. Go to your webhook endpoint
2. Click **Tunnel** in the status bar
3. Enter your local port (e.g., `3000`)
4. Click **Connect**
5. Incoming webhooks now forward to `localhost:3000` automatically

---

## Import from Postman

1. Export your Postman collection as JSON (Collection v2.1)
2. In Kite, open the collection panel (`Cmd+1`)
3. Click the import icon or drag the JSON file into the window
4. Your requests, folders, and variables are imported

Also supports: Bruno, Insomnia, OpenAPI 3.x specs, and cURL commands.

---

## Environments & variables

1. Click the environment switcher in the bottom status bar
2. Create a new environment (e.g., "Development", "Staging")
3. Add variables: `baseUrl` = `http://localhost:3000`
4. Use `{{baseUrl}}` in any URL, header, or body field
5. Switch environments to change all variables at once

Variables support 5 levels of nesting: `{{{{nested}}}}` resolves inner variables first.

---

## Keyboard shortcuts

| Action | Shortcut |
|--------|----------|
| New tab | `Cmd+T` |
| Close tab | `Cmd+W` |
| Send request | `Cmd+Enter` |
| Command palette | `Cmd+K` |
| API client | `Cmd+1` |
| Webhooks | `Cmd+3` |
| SSH | `Cmd+5` |
| Settings | `Cmd+,` |

Full list: [Keyboard Shortcuts](shortcuts.md)

---

## Auto-updates

Kite checks for updates automatically. When a new version is available, you'll see a notification in the status bar. Click to download and install — the app restarts with the new version.

All updates are cryptographically signed. Kite verifies the signature before installing.

---

## Next steps

- [API Client guide](api-client.md) — collections, scripts, test assertions
- [Webhooks guide](webhooks.md) — provider parsing, replay, diff viewer
- [SSH guide](ssh.md) — terminal, SFTP, port forwarding, run-from-remote
- [Monitoring guide](monitoring.md) — alerts, health dashboard

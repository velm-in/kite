<p align="center">
  <img src="https://raw.githubusercontent.com/velm-in/kite/main/assets/kite-logo.png" alt="Kite" width="100" />
</p>

<h1 align="center">Kite</h1>

<p align="center">
  <strong>API client + webhook inspector + localhost tunnel + SSH terminal.</strong><br/>
  One app. Free forever. No account required.
</p>

<p align="center">
  <a href="https://github.com/velm-in/kite/releases/latest"><img src="https://img.shields.io/github/v/release/velm-in/kite?style=flat-square&color=f97316" alt="Latest Release" /></a>
  <a href="https://github.com/velm-in/kite/releases"><img src="https://img.shields.io/github/downloads/velm-in/kite/total?style=flat-square&color=10b981" alt="Downloads" /></a>
  <a href="https://github.com/velm-in/kite/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue?style=flat-square" alt="License" /></a>
  <a href="https://kite.velm.in"><img src="https://img.shields.io/badge/website-kite.velm.in-orange?style=flat-square" alt="Website" /></a>
</p>

<p align="center">
  <a href="https://github.com/velm-in/kite/releases/latest">Download</a> ·
  <a href="https://kite.velm.in">Website</a> ·
  <a href="docs/getting-started.md">Docs</a> ·
  <a href="https://github.com/velm-in/kite/issues">Report Bug</a>
</p>

---

## The problem

You're debugging a webhook integration. You open Postman to send a request. ngrok to expose localhost. webhook.site to inspect the payload. Then Datadog to know when it breaks in prod.

Four tools. Four tabs. Four subscriptions.

**Kite replaces all of them.**

<p align="center">
  <img src="https://raw.githubusercontent.com/velm-in/kite/main/assets/screenshot-api-client.png" alt="Kite — API Client" width="800" />
</p>

---

## Download

| Platform | Architecture | Download |
|----------|-------------|----------|
| macOS | Apple Silicon (M1+) | [Download .dmg](https://github.com/velm-in/kite/releases/latest) |
| macOS | Intel | [Download .dmg](https://github.com/velm-in/kite/releases/latest) |
| Windows | x64 | [Download .msi](https://github.com/velm-in/kite/releases/latest) |
| Linux | x64 | [Download .AppImage](https://github.com/velm-in/kite/releases/latest) |
| Linux | x64 | [Download .deb](https://github.com/velm-in/kite/releases/latest) |

> Free forever for local features. No account required.

---

## What it does

### Send requests <sub>replaces Postman</sub>

Full API client with collections, environments, and variables. Import your Postman collections in one drag. Native HTTP client — no CORS, no proxy hacks.

- HTTP, WebSocket, MQTT, Socket.IO, GraphQL
- Variable substitution with `{{env}}` syntax, 5-level nesting
- Pre/post request scripts with test assertions
- Cookie jar, request history, batch runner

<p align="center">
  <img src="https://raw.githubusercontent.com/velm-in/kite/main/assets/screenshot-collections.png" alt="Kite — Collections" width="800" />
</p>

### Receive webhooks <sub>replaces webhook.site</sub>

Get a permanent URL. Every payload is captured, parsed, and displayed as a human-readable card — not a wall of raw JSON.

- Auto-detects Stripe, GitHub, Twilio, Shopify
- Structured event cards with amounts, emails, statuses at a glance
- Endpoints stay active 24/7, even when the app is closed
- Compare any two payloads with a built-in diff viewer

### Forward to localhost <sub>replaces ngrok</sub>

Built-in tunnel forwards webhooks to your dev server. No separate terminal. No rotating URLs. Click replay to resend any webhook with the exact same payload.

- One-click tunnel to any local port
- Replay any webhook instantly — fix, replay, repeat
- No session limits on Pro

### SSH & run from remote <sub>replaces Termius</sub>

Built-in terminal with SSH host management. Send API requests FROM your staging server to solve IP whitelisting and geo-restrictions without leaving Kite.

- Import from `~/.ssh/config` on first launch
- Port forwarding, SFTP file browser, command snippets
- "Send from remote" — execute requests on any connected server

<p align="center">
  <img src="https://raw.githubusercontent.com/velm-in/kite/main/assets/screenshot-ssh.png" alt="Kite — SSH Terminal" width="800" />
</p>

### Monitor & alert <sub>replaces Datadog</sub>

Health dashboard with volume, success rates, and latency. Alerts hit your Slack before customers hit your inbox.

- Endpoint quiet, forward failing, payload anomaly, signature invalid
- Email, Slack, in-app, and webhook notification channels
- Endpoints stay active 24/7 even when the app is closed

---

## Quick start

```
1. Open Kite → Create an endpoint → get a permanent webhook URL
2. Trigger an event (Stripe payment, GitHub push, etc.) → watch it land in real time
3. Click "Forward" → webhooks route to your localhost automatically
4. Fix your handler → hit "Replay" → same payload, instant feedback
```

See the full [Getting Started guide](docs/getting-started.md).

---

## How it's built

Kite is a [Tauri 2](https://v2.tauri.app/) desktop app. The frontend is React 19. All computation — HTTP requests, JSON parsing, SSH connections, webhook forwarding, collection sync — runs in Rust.

| Layer | Tech |
|-------|------|
| Shell | Tauri 2 (Rust) |
| Frontend | React 19 + Tailwind CSS 4 |
| HTTP engine | reqwest with connection pooling |
| JSON engine | simd-json (SIMD-accelerated parsing) |
| SSH/SFTP | russh |
| WebSocket | tokio-tungstenite |
| MQTT | rumqttc |
| Mock server | hyper |
| State | Zustand |

TypeScript is a display layer. Rust does the work.

---

## Local data, your machine

Collections are saved as `.kite` files on your filesystem. Commit them to Git alongside your code. No cloud dependency for core features.

```
my-project/
├── src/
├── api-collection.kite        ← your API requests
├── api-collection.kite.env.json  ← environment variables
└── ...
```

Import from Postman, Bruno, Insomnia, and OpenAPI specs. Export to cURL.

---

## Pricing

| | Free | Pro — ₹499/mo | Team — ₹1,900/mo |
|---|---|---|---|
| API client | Full | Full | Full |
| Webhook endpoints | 1 | 10 | 50 |
| Webhook history | 50 events, 24h | Unlimited, 90d | Unlimited, 90d |
| Tunnel | 2h sessions | Unlimited | Unlimited |
| SSH hosts | 2 hosts, 1 session | 20 hosts, 5 sessions | Unlimited |
| Alerts | In-app | Email + Slack | All channels |
| Cloud sync | — | Auto-sync | Full sync + conflict resolution |
| Workspaces | — | — | 5 seats, shared collections |
| Account required | No | Yes | Yes |

Free is free forever. No credit card. No trial expiry.

---

## Documentation

| Doc | Description |
|-----|-------------|
| [Getting Started](docs/getting-started.md) | Install, first endpoint, first request |
| [API Client](docs/api-client.md) | Requests, collections, environments, variables, scripts |
| [Webhooks](docs/webhooks.md) | Endpoints, event inspection, provider parsing, replay |
| [Tunneling](docs/tunneling.md) | Localhost forwarding, custom subdomains |
| [SSH & Remote](docs/ssh.md) | Terminal, host management, SFTP, port forwarding, run-from-remote |
| [Monitoring](docs/monitoring.md) | Health dashboard, alert rules, notification channels |
| [Import & Export](docs/import-export.md) | Postman, Bruno, Insomnia, OpenAPI, cURL |
| [Keyboard Shortcuts](docs/shortcuts.md) | All shortcuts and command palette |
| [Auto-Updates](docs/auto-updates.md) | How signed updates work |

---

## Comparison

You'd need Postman + ngrok + webhook.site + a monitoring tool to match what Kite does alone. That's $40–70/month vs ₹0–499.

| Feature | Kite | Postman | ngrok | webhook.site |
|---------|------|---------|-------|-------------|
| API client | Yes | Yes | — | — |
| Webhook inspection | Yes | — | — | Yes |
| Localhost tunnel | Yes | — | Yes | — |
| Webhook replay | Yes | — | — | — |
| SSH terminal | Yes | — | — | — |
| Run-from-remote | Yes | — | — | — |
| Provider parsing | Yes | — | — | — |
| Payload diff | Yes | — | — | — |
| Health monitoring | Yes | — | — | — |
| Offline-first | Yes | — | — | — |
| Git-friendly files | Yes | — | — | — |
| Free tier | Full app | Limited | Limited | Limited |

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

Found a bug? [Open an issue](https://github.com/velm-in/kite/issues/new?template=bug_report.md).
Have an idea? [Request a feature](https://github.com/velm-in/kite/issues/new?template=feature_request.md).

---

## Security

Kite auto-updates are signed with a public/private key pair. Every release binary is verified against the embedded public key before installation. If you find a security vulnerability, please email security@velm.in instead of opening a public issue.

---

## License

[MIT](LICENSE)

---

<p align="center">
  <sub>Built by <a href="https://velm.in">Velm</a></sub>
</p>

# Tunneling

Kite's built-in tunnel forwards webhooks from your cloud endpoint to your local development server. No separate tool, no rotating URLs.

---

## How it works

```
External service (Stripe, GitHub, etc.)
    │
    ▼
Kite cloud endpoint (kite.velm.in/wh/<slug>)
    │
    ▼ WebSocket relay
    │
Kite desktop app
    │
    ▼ HTTP proxy
    │
localhost:<your-port>
```

1. Kite opens a persistent WebSocket connection to the server
2. When a webhook arrives at your endpoint, the server forwards it through the WebSocket
3. Kite proxies the webhook to your local server
4. Your server's response flows back through the WebSocket to the original webhook sender

---

## Starting a tunnel

1. Create a webhook endpoint (if you don't have one)
2. Click the **Tunnel** indicator in the status bar
3. Enter your target: `localhost` and port (e.g., `3000`)
4. Click **Connect**

The status bar shows the active tunnel: `kite.velm.in/wh/k7x9m2p1 → localhost:3000`

---

## Session limits

| Plan | Session limit |
|------|--------------|
| Free | 2 hours per session |
| Pro | Unlimited |
| Team | Unlimited |

Free sessions disconnect after 2 hours. Reconnect to start a new session.

---

## Custom subdomains

Pro and Team plans get a stable custom subdomain:

```
https://<your-slug>.kite.velm.in
```

This URL never changes, so you don't need to update webhook configurations in external services.

---

## Replay through tunnel

When your tunnel is active, replaying a webhook sends it through the tunnel to your local server. This means you can:

1. Receive a webhook
2. See it fail against your local handler
3. Fix the bug
4. Replay the exact same webhook
5. Verify the fix

All without triggering a new event in the external service.

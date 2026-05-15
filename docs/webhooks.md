# Webhooks

Kite gives you a permanent URL to receive, inspect, and replay webhooks from any service.

---

## Creating an endpoint

1. Go to **Webhooks** (`Cmd+3`)
2. Click **Create Endpoint**
3. Your endpoint URL is generated: `https://kite.velm.in/wh/<slug>`
4. Paste this URL in your service's webhook settings (Stripe, GitHub, etc.)

Endpoints stay active 24/7 — even when Kite is closed. Webhooks are stored on the server and synced when you open the app.

### Limits by plan

| Plan | Endpoints | History |
|------|-----------|---------|
| Free | 1 | 50 events, 24h retention |
| Pro | 10 | Unlimited, 90 days |
| Team | 50 | Unlimited, 90 days |

---

## Inspecting events

When a webhook arrives, it appears in real time in the event list. Each event shows:

- **Timestamp** — when it was received
- **Method** — POST, GET, etc.
- **Status** — delivery status
- **Provider** — auto-detected source (Stripe, GitHub, Twilio)
- **Headers** — full request headers
- **Body** — parsed payload

### Provider detection

Kite automatically identifies and parses webhooks from:

| Provider | Detection | Parsed fields |
|----------|-----------|---------------|
| **Stripe** | `stripe-signature` header | Event type, amount, currency, customer, status |
| **GitHub** | `x-github-event` header | Repository, action, actor, ref |
| **Twilio** | Twilio-specific headers | Message SID, from, to, status |

Generic webhooks show raw headers and body with JSON syntax highlighting.

---

## Replay

Found a bug in your handler? Fix it and replay the exact same payload.

1. Select any webhook event
2. Click **Replay** (or right-click > Replay)
3. Choose target: original endpoint or custom URL
4. The webhook is re-sent with the same headers, body, and method

No more triggering fake Stripe payments or pushing empty commits to test your handler.

---

## Diff viewer

Compare any two webhook payloads side by side.

1. Select a webhook event
2. Click **Compare** (or right-click > Compare with...)
3. Select the second event
4. Side-by-side diff highlights added, removed, and changed fields

Spot changes in amounts, statuses, or new fields instantly.

---

## Forwarding to localhost

See [Tunneling](tunneling.md) for full details.

Quick version:
1. Click **Tunnel** in the status bar
2. Enter your local port
3. Incoming webhooks auto-forward to your dev server
4. Responses flow back to the webhook sender

---

## Filtering & search

- **Filter by provider**: Show only Stripe, GitHub, or Twilio events
- **Filter by status**: Success, error, forwarded
- **Search**: Full-text search across headers and body
- **Time range**: Filter by date/time range

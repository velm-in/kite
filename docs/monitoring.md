# Monitoring & Alerts

Kite monitors your webhook endpoints 24/7 and alerts you when something goes wrong — before your users notice.

---

## Health dashboard

The health dashboard shows real-time metrics for each endpoint:

| Metric | Description |
|--------|-------------|
| **Webhooks received** | Total count in the last 24h |
| **Success rate** | Percentage of webhooks processed without errors |
| **P95 latency** | 95th percentile response time |
| **Volume chart** | 7-day trend of webhook volume |
| **Status** | Healthy, degraded, or down |

Metrics are aggregated hourly and retained for 90 days.

---

## Alert rules

Set up rules to get notified when endpoints need attention.

| Alert type | Triggers when |
|------------|--------------|
| **Endpoint quiet** | No webhooks received for a configured period |
| **Forward failing** | Localhost forwarding returns errors 3+ times in a row |
| **Signature invalid** | Webhook signature verification fails |

### Creating an alert

1. Go to **Health** > **Alerts**
2. Click **New Rule**
3. Select the endpoint, alert type, and threshold
4. Choose notification channels
5. Save

---

## Notification channels

| Channel | Plans |
|---------|-------|
| In-app | Free, Pro, Team |
| Email | Pro, Team |
| Slack | Pro, Team |
| Webhook | Team |

### Slack integration

1. Go to Settings > Notifications
2. Enter your Slack webhook URL
3. Alerts are posted to the configured channel

### Webhook notifications

Team plans can send alert notifications to any URL — integrate with PagerDuty, Opsgenie, Discord, or your own systems.

---

## Availability

| Plan | Dashboard | Alerts |
|------|-----------|--------|
| Free | — | In-app only |
| Pro | Full dashboard, 90-day history | Email + Slack |
| Team | Full dashboard, 90-day history | All channels |

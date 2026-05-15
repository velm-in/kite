# SSH & Remote Execution

Kite includes a full SSH terminal, SFTP file browser, port forwarding, and the ability to run API requests from remote servers.

<p align="center">
  <img src="https://raw.githubusercontent.com/velm-in/kite/main/assets/screenshot-ssh.png" alt="Kite — SSH Terminal" width="700" />
</p>

---

## SSH terminal

A built-in terminal emulator for SSH connections. No need for a separate terminal app.

### Adding hosts

1. Go to **SSH** (`Cmd+5`)
2. Click **Add Host**
3. Enter hostname, port, username, and auth method
4. Choose: password, private key, or key file

On first launch, Kite imports hosts from `~/.ssh/config` automatically.

### Connecting

Click any host to open an SSH terminal session. Multiple sessions can run in parallel across different tabs.

### Trust On First Use (TOFU)

First connection to a new host auto-accepts the fingerprint. If a host's fingerprint changes (potential MITM), Kite blocks the connection. Use **Forget Host** to re-trust.

### Limits

| Plan | Hosts | Concurrent sessions |
|------|-------|-------------------|
| Free | 2 | 1 |
| Pro | 20 | 5 |
| Team | Unlimited | Unlimited |

---

## Run from remote

Send API requests from a remote server instead of your local machine. Solves:

- **IP whitelisting** — hit APIs that only allow server IPs
- **Geo-restrictions** — test from servers in different regions
- **Production debugging** — curl from staging/prod without SSH + manual commands

### How to use

1. Open a request tab
2. Click the server icon next to **Send**
3. Select a connected SSH host
4. Click **Send from Remote**

The request executes on the remote server. The response is displayed in Kite as if it ran locally.

---

## Port forwarding

Forward ports between your local machine and remote servers over SSH.

### Local forwarding

Access a remote service on a local port:
```
localhost:5432  →  remote-db:5432
```
Use case: Connect your local database client to a remote PostgreSQL server.

### Remote forwarding

Expose a local service on the remote server:
```
remote:8080  →  localhost:3000
```
Use case: Let a remote server access your local dev server.

### Managing forwards

Active port forwards are shown in the status bar. Click to view, add, or remove forwards.

---

## SFTP

Browse and manage files on remote servers.

- Navigate directories
- Upload and download files
- Create, rename, and delete files/folders
- View file contents

Access SFTP from the SSH panel for any connected host.

---

## Snippets

Save frequently used SSH commands as snippets.

1. Go to SSH > Snippets
2. Click **Add Snippet**
3. Name it and enter the command
4. Click to execute on any connected host

Team plans support shared snippet libraries across workspace members.

# API Client

Kite's API client replaces Postman for sending and organizing HTTP requests. Native Rust HTTP engine — no CORS issues, no browser limitations.

---

## Protocols

| Protocol | Description |
|----------|-------------|
| HTTP/HTTPS | Full HTTP client with HTTP/2, compression (gzip, brotli, deflate), cookies |
| WebSocket | Connect, send/receive messages, view frame history |
| GraphQL | Query editor with schema introspection |
| MQTT | Publish/subscribe to topics |
| Socket.IO | Connect and emit/listen to events |

---

## Sending a request

1. Select method (GET, POST, PUT, PATCH, DELETE, HEAD, OPTIONS)
2. Enter URL — supports `{{variables}}`
3. Configure headers, query params, body, and auth
4. Press **Send** (`Cmd+Enter`)

The response panel shows: status code, response time, size, headers, and body (auto-formatted JSON).

---

## Request body

| Type | Description |
|------|-------------|
| JSON | CodeMirror editor with syntax highlighting and formatting |
| Form Data | Key-value pairs, supports file uploads |
| URL Encoded | Key-value pairs, URL-encoded |
| Raw | Plain text, XML, HTML, etc. |
| Binary | File upload |
| None | No body (GET, HEAD, DELETE) |

---

## Authentication

| Type | Description |
|------|-------------|
| Bearer Token | `Authorization: Bearer <token>` |
| Basic Auth | Username + password, base64 encoded |
| JWT | Generate JWTs with custom claims and signing algorithms |
| AWS Signature v4 | Sign requests for AWS services |
| Digest Auth | Challenge-response authentication |
| API Key | Key in header or query parameter |

---

## Collections

Collections organize requests into folders. Saved as `.kite` files on your filesystem.

```
my-project/
├── api-collection.kite          ← requests + folders
├── api-collection.kite.env.json ← environment variables
└── src/
```

### Operations

- **Create**: Right-click in collection panel > New Collection
- **Folders**: Nest requests in folders, unlimited depth
- **Drag & drop**: Reorder requests and folders
- **Duplicate**: `Cmd+D` on any request
- **Delete**: Right-click > Delete (or `Backspace`)

### Import

| Source | Format |
|--------|--------|
| Postman | Collection v2.1 JSON |
| Bruno | Bruno collection directory |
| Insomnia | Insomnia export JSON |
| OpenAPI | OpenAPI 3.x YAML/JSON |
| cURL | Single cURL command |

### Export

- Export to cURL command
- Export collection as `.kite` file

---

## Environments & variables

Environments are sets of key-value pairs. Switch between them to change all `{{variables}}` at once.

```
Development:
  baseUrl = http://localhost:3000
  apiKey  = dev_key_123

Staging:
  baseUrl = https://staging.myapp.com
  apiKey  = stg_key_456
```

### Variable resolution

Variables use `{{name}}` syntax and resolve from the active environment. Supports:

- **Nesting**: `{{{{dynamicKey}}}}` — resolves inner variable first
- **Depth limit**: 5 levels (prevents circular references)
- **Secret masking**: Mark variables as secret — values are hidden in the UI
- **Batch substitution**: All variables in URL, headers, body, and auth are resolved in one pass (Rust engine)

---

## Pre/post request scripts

Write JavaScript scripts that run before sending a request or after receiving a response.

**Pre-request**: Set variables, generate timestamps, compute signatures.

**Post-response**: Extract values, run test assertions, chain requests.

---

## Test runner

Run all requests in a collection sequentially with the batch runner.

1. Open command palette (`Cmd+K`) > "Run Collection"
2. Select collection and environment
3. View pass/fail results for each request

---

## Request history

Last 100 requests are saved automatically. Access from the History panel.

- Search by URL, method, or status code
- Click to re-open any historical request
- URL autocomplete suggests from history (trie-based, Rust engine)

---

## Cookie jar

Cookies from responses are automatically captured and stored per domain. They're sent with subsequent requests to the same domain — just like a browser.

View and manage cookies from Settings > Cookies.

---

## Mock server

Start a local mock server to simulate API responses without a backend.

1. Open command palette > "Mock Server"
2. Add routes with method, path, status code, and response body
3. Start on any port (default: 4001)
4. Hit `localhost:4001/your-route` — get your mock response

Supports dynamic responses, delays, and header matching.

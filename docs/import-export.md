# Import & Export

Bring your existing API collections into Kite, or export Kite collections for use elsewhere.

---

## Import

### Postman

1. In Postman, export your collection as **Collection v2.1** JSON
2. In Kite, open the collection panel (`Cmd+1`)
3. Click the import icon or drag the `.json` file into the window
4. Requests, folders, and variables are imported

Kite preserves folder structure, request names, headers, body, auth settings, and pre-request scripts.

### OpenAPI / Swagger

1. Prepare your OpenAPI 3.x spec (`.yaml` or `.json`)
2. Drag into Kite or use Import > OpenAPI
3. Each endpoint becomes a request, organized by tags into folders

### Bruno

1. Point Kite to your Bruno collection directory
2. Kite reads `.bru` files and converts them to Kite requests

### Insomnia

1. Export from Insomnia as JSON
2. Import into Kite — workspaces become collections

### cURL

Paste a cURL command anywhere in the URL bar. Kite parses it into a full request with method, headers, body, and auth.

---

## Export

### cURL

Right-click any request > **Copy as cURL**. The generated command includes all headers, body, and auth.

### .kite files

Collections are already stored as `.kite` files on your filesystem. Copy them to share with teammates or commit to Git.

```
my-api.kite              ← collection file
my-api.kite.env.json     ← environment variables
```

---

## File format

`.kite` files are JSON with a defined schema:

```json
{
  "name": "My API",
  "requests": [
    {
      "name": "Get Users",
      "method": "GET",
      "url": "{{baseUrl}}/users",
      "headers": [],
      "body": null
    }
  ],
  "folders": [
    {
      "name": "Auth",
      "requests": [...],
      "folders": [...]
    }
  ]
}
```

Collections can be nested to any depth. Environment files store variables separately so you can gitignore secrets while committing the collection.

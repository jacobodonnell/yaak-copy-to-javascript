# Copy as JavaScript (fetch) — Yaak Plugin

A Yaak plugin that copies an API request as JavaScript using the native Fetch API.

- Minimal, readable output
- Preserves method, URL, headers, and body
- Safe JSON handling with JSON.stringify

Status: Early version. Works for typical JSON and form-encoded requests; multipart has a TODO.

## Demo

Copy → "Copy as JavaScript (fetch)" on any request in Yaak. Paste into your editor.

## Installation (development)

1) Prereqs
- Node.js 18+
- Yaak desktop app

2) Install deps

```
npm install
```

3) Build

```
npm run build
```

4) Load in Yaak
- Use Yaak’s plugin developer flow to load a local plugin (see Yaak docs).

## Usage
- In Yaak, select a request → Copy → Copy as JavaScript (fetch)
- Snippet rules:
  - Only includes `method` when not GET
  - Only includes `headers` if present
  - JSON bodies: attempts to pretty-print via `JSON.stringify(object)`; falls back to string
  - x-www-form-urlencoded: passes raw text or suggests `URLSearchParams`
  - multipart/form-data: leaves a TODO to build `FormData`

## Examples

- GET

```js
fetch("https://api.example.com/users");
```

- POST JSON

```js
fetch("https://api.example.com/users", {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify({
    name: "John Doe",
    email: "john@example.com"
  }),
});
```

## Limitations
- Multipart FormData is not yet constructed automatically
- Binary bodies are not handled; falls back to raw string when possible

## Development Notes
- Keep output deterministic and easy to diff
- Prefer explicit over implicit: only include headers/body when necessary

## License
MIT


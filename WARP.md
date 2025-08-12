# copy-as-javascript (Yaak Plugin)

Purpose
- A Yaak plugin that copies an API request as JavaScript using the Fetch API.

What it does
- Adds a "Copy as JavaScript (fetch)" action to Yaak requests.
- Generates a minimal, readable fetch snippet that preserves method, URL, headers, query params, and body.

Usage
- In Yaak, select a request and choose: Copy → Copy as JavaScript (fetch).
- Paste the generated code into your editor or docs.

Output style
- Uses native fetch.
- Avoids unnecessary dependencies.
- Formats headers and body safely (e.g., JSON.stringify for JSON bodies).

Notes for development
- Keep output deterministic and easy to diff.
- Prefer explicit over implicit: only include headers/body when necessary.
- Consider handling edge cases (binary bodies, multipart, FormData) gracefully with clear fallbacks.

Scope
- This plugin focuses solely on producing fetch-based JavaScript output.
- It does not execute requests or manage authentication.

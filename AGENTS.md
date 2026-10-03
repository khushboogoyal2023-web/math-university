# AGENTS.md

## Project Overview
Single-file static HTML app (`github_pages_live_dns_hub.html`) — a client-side DNS/CNAME management tool (Hindi UI) using Tailwind CSS (CDN) and localStorage. No backend, no build step, no external dependencies or credentials.

## Running in Base44
- Served by `nginx:alpine` via `docker-compose.base44.yml` on host port 3000.
- The HTML file is NOT named `index.html`, so a custom nginx config (`nginx.default.conf`) sets it as the index, and `nginx.main.conf` overrides the default to run workers as `root` (the bind-mounted host directory has restrictive 700 permissions).
- No live-reload dev server; call `reload_preview` after edits to the HTML file.
- No secrets required.

## Verification
- `curl -s -o /dev/null -w "%{http_code}" http://localhost:3000/` should return `200`.
- The page title is "GitHub Pages & Live DNS Hub".

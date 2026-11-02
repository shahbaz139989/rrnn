# CORE panel

FastAPI admin panel and WebSocket-to-TCP gateway.

## Runtime configuration

Set ADMIN_PASSWORD (at least 12 characters) and SECRET_KEY before starting. The service fails closed when either is missing. Keep both values in your deployment provider secret store; do not commit them. PORT defaults to 8000.

The panel is same-origin by default, so cross-origin access is disabled. If a separate frontend must call this API, set PANEL_ORIGINS to a comma-separated list of exact origins, including scheme and port where applicable. COOKIE_SECURE defaults to true; set it to false only for local plain-HTTP development.

## Local run

Install requirements.txt, configure the required environment variables, then run: uvicorn app:app --host 0.0.0.0 --port 8000

## Render

render.yaml launches the ASGI app through Uvicorn and asks Render to generate ADMIN_PASSWORD and SECRET_KEY. Retrieve the generated admin password from Render environment settings.

## State and restarts

Link configuration, quota usage, sessions, and runtime statistics are currently held in process memory. A restart or redeploy resets that state; persistent storage is not included in this hardening pass.

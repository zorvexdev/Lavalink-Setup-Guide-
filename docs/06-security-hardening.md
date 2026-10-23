# 06 · Security hardening

## Rotate any public password

The referenced public configuration includes the password `aeroxdevs`. Treat it as disclosed and never reuse it. If a live server has used it, rotate the password immediately, update the bot's secret store, and review access and request logs for unexpected clients.

## Network boundary

- Prefer `server.address: 127.0.0.1` when the bot and node share a host.
- On separate hosts, bind to a private interface and restrict inbound traffic to the bot host or trusted private network.
- Do not expose Lavalink's port directly to arbitrary internet traffic.
- If a reverse proxy is used, configure WebSocket upgrade forwarding, TLS, source-IP restrictions where feasible, and the correct external/internal ports.
- Do not assume that changing the port to a common HTTP port makes the service secure.

## Credentials and OAuth

- Use a high-entropy, unique node password.
- Store secrets in environment variables or a deployment secret store, not in Git.
- Treat YouTube OAuth refresh tokens as credentials. Do not paste them into issues, Discord chats, screenshots, or commit history.
- Use a separate account for OAuth experiments if following the plugin maintainer's warnings, and understand that OAuth may still trigger rate limits or account action.
- If a token was committed or publicly shared, revoke or replace it; deleting the latest file does not erase it from Git history.

## Plugin and remote dependency review

Plugins execute inside your server process and can affect availability and security. Pin versions, inspect upstream repositories and licenses, and update deliberately. A remote cipher service is an additional third-party dependency; verify its maintainer, TLS behavior, availability, privacy and terms before depending on it.

## Request logs and metrics

Disable payload/header logging unless needed for a specific diagnostic task. Metrics endpoints should remain private or be protected by a trusted network boundary. Set sensible file-size and retention limits, and avoid placing credentials in query strings.

## Production minimum

A unique secret, restricted network reachability, supported Java runtime, pinned plugins, private logs, backups of configuration without secrets, and a documented rollback path should all be in place before public use.

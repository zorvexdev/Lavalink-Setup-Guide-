# 14 · Reverse proxy and TLS

A proxy can terminate TLS and route traffic to a private Lavalink listener, but it must support WebSocket upgrades. Lavalink's protocol is not just ordinary short HTTP requests.

## Principles

- Keep Lavalink bound to localhost or a private interface behind the proxy.
- Enable HTTPS/WSS on the public endpoint if traffic crosses an untrusted network.
- Forward the HTTP `Upgrade` and `Connection` headers correctly.
- Use appropriate proxy read/send timeouts for long-lived WebSocket connections.
- Restrict the endpoint to trusted source IPs or VPN paths when possible.
- Preserve the Lavalink authentication requirement; TLS does not replace the password.
- Do not expose administrative or metrics endpoints unnecessarily.

## Validate

1. Test HTTPS reachability from the bot host.
2. Test a WebSocket connection using the actual client library.
3. Confirm the upstream sees the expected requests.
4. Check the proxy log for 400/401/403/502 errors and WebSocket upgrade failures.
5. Confirm that the backend port is not also open directly to the internet.

Use the official API and your proxy's current documentation for exact settings. A generic reverse-proxy snippet may need adaptation for WebSocket and idle-timeout behavior.

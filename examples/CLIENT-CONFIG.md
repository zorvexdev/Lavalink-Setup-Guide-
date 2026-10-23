# Client connection values

Use these settings as a concept, not as a library-specific constructor:

- Host: `127.0.0.1` when the bot is on the same host/container network route; otherwise use a private hostname/IP.
- Port: `2333` in the examples here. Set the same port in the bot and server config.
- Password: read from the same secret store used by Lavalink; never hard-code it in the source tree.
- TLS/WebSocket secure flag: enable it only when the client connects through a correctly configured TLS/WSS endpoint.

If the bot runs in another Compose container, `127.0.0.1` points to the bot container itself, not the Lavalink container. In that case use the service name on a private Docker network and do not publish the port publicly.

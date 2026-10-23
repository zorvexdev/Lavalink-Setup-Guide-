# 04 · Configuration guide

Lavalink v4 reads its configuration from YAML. Use spaces, not tabs, and keep related keys inside their documented parent sections. Incorrect indentation can change the meaning of the configuration or prevent startup.

## Core settings

- `server.port`: TCP port used by the node's HTTP/WebSocket server.
- `server.address`: network interface to bind to. `127.0.0.1` limits access to the local host; `0.0.0.0` listens on all IPv4 interfaces and should only be used with deliberate network controls.
- `lavalink.server.password`: shared secret required by clients.
- `lavalink.server.sources`: toggles built-in source managers. A plugin can replace a built-in source, so avoid enabling duplicate managers without checking plugin docs.
- `lavalink.plugins`: Maven plugin dependency declarations, repositories, and snapshot flags.
- `logging`: console/file log levels and request logging behavior.
- `metrics.prometheus`: optional metrics endpoint. Keep metrics private unless properly protected.

## Environment placeholders

Spring-style placeholders such as `${LAVALINK_SERVER_PASSWORD}` may be used for secrets when supported by the installed version and deployment method. Ensure the variable is actually set in the process environment. An unresolved placeholder can prevent startup; a literal fallback such as `CHANGE_ME` can also accidentally become a live password.

## Request logging

Full request payload logging can leak request data or credentials. Prefer conservative request logging in production. Enable detailed logging temporarily during debugging, then restore the safer level and rotate logs according to your retention policy.

## Version discipline

Pin plugin versions to tested, known-good identifiers. Snapshot builds may change and can require the snapshot Maven repository. After changing one plugin, restart and verify startup logs, track search, track playback, playlists, and recovery after a node restart.

For all keys and their defaults, defer to the [official configuration docs](https://lavalink.dev/configuration/).

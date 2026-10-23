# 17 · Troubleshooting

## Lavalink does not start

- Confirm Java is installed and meets the required version.
- Verify the JAR path and working directory.
- Check YAML indentation and key placement.
- Check plugin repositories, artifact coordinates, and version values.
- Search logs for the first exception, not just the last repeated message.

## Client cannot connect

- Confirm the hostname and port are reachable from the bot's host/container.
- Verify that the listener is bound to an interface reachable from the client.
- Check firewall, security group, Docker network, and proxy rules.
- Confirm the password exactly matches.
- If using WSS/TLS, check certificate validity and WebSocket upgrade handling.

## Search works but playback fails

Search metadata may come from a different provider than the actual playback source. Test the target source independently, inspect provider errors, verify source enablement and plugin compatibility, and try a known playable track.

## Plugin not loaded

Check Maven repository URL, dependency coordinate, `snapshot` setting, upstream availability, and the version's Lavalink compatibility. Avoid changing multiple plugin versions at once.

## YouTube OAuth or source failures

Check the YouTube Source docs, logs, OAuth token validity, supported client order, upstream rate limits, and current service behavior. OAuth does not guarantee that all requests will succeed.

## Audio stops or gets stuck

Inspect node CPU/memory, source/network errors, and stuck-track thresholds. Test another source to distinguish a global node problem from an upstream provider problem. Keep reconnect loops bounded.

## Port is already in use

Choose a free port, update the Lavalink server config, firewall/proxy mapping, and bot client config together. Do not switch to port 80 without checking what already owns it and whether the node should be exposed there.

## Helpful upstream pages

- [Official troubleshooting](https://lavalink.dev/getting-started/troubleshooting)
- [Official FAQ](https://lavalink.dev/getting-started/faq)
- [Official configuration](https://lavalink.dev/configuration/)

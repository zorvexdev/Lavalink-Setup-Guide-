# 10 · Node.js client integration

Use a maintained Lavalink client with explicit Lavalink v4 support. The snippet below illustrates configuration shape only; adapt it to the specific library's current API.

## Connection values

Keep these in environment variables:

```env
LAVALINK_HOST=127.0.0.1
LAVALINK_PORT=2333
LAVALINK_PASSWORD=replace-with-a-long-random-secret
```

Never put the password in a public repository or share it in client-side code. A Discord bot usually runs server-side, but secrets still need to be excluded from logs and commits.

## Connection checklist

- Host and port match the node's listener or private proxy route.
- Password matches the server's configured secret exactly.
- Client library version supports your Lavalink server version.
- WebSocket reachability works from the bot host.
- Node logs show an accepted connection and the client reports ready.
- Track search and playback are tested after connection, not just the connection event.

## Example using a Lavalink client

Refer to the official client documentation for the exact API and event model: [Lavalink client](https://github.com/lavalink-devs/Lavalink-Client). Do not mix constructor and event examples from different major releases. Most clients need a node descriptor containing an identifier, host, port, password, and a secure-connection flag as appropriate for your topology.

## Production behavior

Use bounded retries with backoff, reconnect handling, health checks, and a clear user-facing error when the node is unavailable. Avoid aggressive reconnection loops that amplify a transient outage. When multiple nodes are used, ensure node selection considers availability and player state rather than merely choosing the first array element.

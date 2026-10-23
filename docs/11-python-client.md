# 11 · Python client integration

For Python bots, choose a maintained client that supports the Lavalink version deployed. Wavelink is one commonly used option with `discord.py`; always check its current compatibility matrix and docs before upgrading.

- [Wavelink docs](https://wavelink.readthedocs.io/)
- [Lavalink API docs](https://lavalink.dev/api/)

## Configuration pattern

Load host, port and password from environment variables or a secret manager. Do not commit a real `.env` file. Keep a `.env.example` with placeholder values only.

```env
LAVALINK_HOST=127.0.0.1
LAVALINK_PORT=2333
LAVALINK_PASSWORD=replace-with-a-long-random-secret
```

## Integration checklist

1. Confirm the library supports the server and Python versions in your deployment.
2. Connect after the Discord client has initialized the events required by your library.
3. Handle node-ready, disconnect, exception, and track-end events.
4. Test a search and playback path from a voice channel.
5. Test node recovery and user-facing errors when the Lavalink process is restarted.

## Operational notes

Library APIs and event names differ across versions. Do not copy old Wavelink code into a newer release without checking the migration guide. Keep Discord connection lifecycle and Lavalink connection lifecycle distinct in your bot design.

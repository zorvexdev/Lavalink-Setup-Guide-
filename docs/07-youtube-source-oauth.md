# 07 · YouTube Source and OAuth

The YouTube Source plugin replaces Lavalink's built-in YouTube source. For Lavalink v4, the plugin dependency is declared under `lavalink.plugins`, and the built-in source is normally disabled with `lavalink.server.sources.youtube: false`.

## Enable the plugin

Use the exact dependency version and repository format from the current [YouTube Source README](https://github.com/lavalink-devs/youtube-source). Snapshot builds should use a version identifier provided by the project's own release/commit process and the snapshot repository. Do not blindly copy an old hash into a new deployment.

A minimal plugin section resembles:

```yaml
plugins:
  youtube:
    enabled: true
    allowSearch: true
    allowDirectVideoIds: true
    allowDirectPlaylistIds: true
    clients:
      - WEB
      - ANDROID_VR
```

Use only client identifiers supported by the exact plugin version. Client ordering matters, and different clients offer different loading, playback, OAuth, and metadata capabilities.

## First OAuth flow

1. In the YouTube plugin configuration, enable OAuth and leave `refreshToken` unset.
2. Do not set `skipInitialization: true` before the first flow unless you intend to add a token later.
3. Start Lavalink and watch the console. The plugin provides instructions for completing its device authorization flow.
4. Complete the flow only through the legitimate URL/instructions provided by the plugin.
5. Capture the refresh token from the server console and store it as a secret.
6. Stop Lavalink, provide the refresh token through a protected configuration source, and enable skip-initialization as documented by the plugin.
7. Restart and confirm that OAuth initializes successfully.

The exact YAML shape can change; consult the upstream plugin README before deployment. The refresh token is sensitive. Redact it from terminal history, CI logs, container output, and backups shared with others.

## Limits and cautions

OAuth is not a guarantee against rate limits, bot checks, playback failures, or account action. Follow the plugin maintainer's current warnings and service terms. Never use your primary account for experiments when the upstream project advises using a separate test account.

## Troubleshooting

- Missing OAuth instructions: check `dev.lavalink.youtube.http.YoutubeOauth2Handler` logging and plugin startup output.
- Repeated sign-in prompts: verify whether a refresh token was actually persisted and whether it is valid.
- Searches work but playback fails: test a different supported client and compare its capabilities.
- HTTP 429 or verification challenges: reduce request rate and follow the provider/plugin's guidance rather than assuming that changing a token will solve everything.

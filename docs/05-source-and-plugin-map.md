# 05 · Source and plugin map

The referenced setup combines built-in Lavalink sources with separate plugin-based providers. These are distinct systems: disabling a built-in source does not necessarily disable a plugin source with a similar name.

## Built-in sources in the referenced setup

| Source | Configured state | Notes |
| --- | --- | --- |
| Bandcamp | Enabled | Built-in source manager |
| HTTP | Enabled | For permitted direct HTTP audio URLs |
| Local files | Disabled | Keep disabled unless local-file support is specifically needed and the environment is trusted |
| NicoNico | Enabled | Built-in source manager |
| SoundCloud | Enabled | Built-in source manager |
| Twitch | Enabled | Built-in source manager |
| Vimeo | Enabled | Built-in source manager |
| Built-in YouTube | Disabled | YouTube Source plugin is used instead |

## Plugin-provided capabilities

- **YouTube Source:** YouTube-specific source manager, with client, OAuth, and cipher options.
- **PulseLink:** Additional provider/search integration for services such as Spotify, Apple Music, Tidal, JioSaavn, Audiomack, Gaana, SoundCloud, and Pandora, depending on plugin version and config.
- **LavaSearch:** An advanced search plugin; it is not itself a universal playback backend.

Provider availability changes with plugin releases, regional restrictions, upstream API changes, credentials, and terms. Treat status tables as configuration snapshots, not guarantees of long-term availability.

## Rule of thumb

Confirm a feature in three places: the current plugin README, the exact version being loaded, and the live startup logs. A YAML value can be syntactically accepted even if the provider later fails to resolve a track.

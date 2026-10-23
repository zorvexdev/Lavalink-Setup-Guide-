# 09 · LavaSearch

LavaSearch is an advanced search plugin for compatible Lavalink v4 deployments. It can enrich search behavior when compatible search managers are available, but it should not be mistaken for a complete playback source or a replacement for a source plugin.

## Install

Use the dependency coordinate and version published by [LavaSearch](https://github.com/topi314/LavaSearch). The project documents a Maven release repository and examples for plugin mode. Match the dependency version to your deployed Lavalink version.

## Configure search sources

An example matching the referenced setup is:

```yaml
plugins:
  lavasearch:
    sources:
      - spotify
      - youtube
```

Supported source identifiers are version-specific. Some search sources depend on other plugins or integrations being available. Follow the upstream example for the exact release installed.

## Validation

1. Start Lavalink and confirm LavaSearch is loaded in the logs.
2. Run a search using the client library's supported search API/prefixes.
3. Test a track, playlist, album, and artist only where those result types are supported.
4. Test the fallback path used by the bot when search returns no results.

## Common confusion

A successful LavaSearch query does not prove that a matching track can be played. Search metadata, URI resolution, and actual source playback are separate operations and should be observed independently.

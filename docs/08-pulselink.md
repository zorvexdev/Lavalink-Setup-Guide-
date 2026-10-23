# 08 · PulseLink

PulseLink is a third-party plugin that can add source/provider integrations to a Lavalink setup. Provider names, setup requirements, and supported options are release-specific. Read the [upstream PulseLink repository](https://github.com/ItzRandom23/PulseLink) for the version you install.

## Dependency setup

Declare the plugin under `lavalink.plugins` using the exact artifact coordinate, repository, and version shown by upstream. Do not use an unpinned `latest`, wildcard, or guessed version. JitPack coordinates may be sensitive to repository/tag naming, so copy the upstream declaration and then test it.

## Provider configuration

The referenced config enabled several providers and disabled others requiring credentials or unavailable executables. An illustrative fragment is:

```yaml
plugins:
  pulselink:
    providers:
      - "ytsearch:%ISRC%"
      - "ytsearch:%QUERY%"
    sources:
      spotify: true
      applemusic: true
      tidal: true
      jiosaavn: true
      audiomack: true
      gaana: true
      soundcloud: true
      pandora: true
      deezer: false
      qobuz: false
      ytdlp: false
```

This is an example, not a guarantee that every entry is accepted by every PulseLink release. Verify source identifiers and provider-specific requirements upstream.

## Spotify-style mirroring

A provider may search for a matching track on a separate playable source using identifiers such as ISRC or a normalized query. That behavior is track resolution/mirroring, not the same as having direct playback access to the original streaming service. Check the provider's functionality and applicable terms.

## Debugging

- Confirm the plugin was downloaded and loaded at startup.
- Check the plugin's own config examples for renamed keys.
- Start with one provider enabled and test a simple track before enabling the full list.
- Disable a failing provider temporarily rather than masking all provider errors.
- Do not share client IDs, API keys, access tokens, or private credentials when posting logs.

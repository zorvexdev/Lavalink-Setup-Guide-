# 01 · Lavalink overview

## What Lavalink does

Lavalink is a separate audio node that handles audio loading, decoding, buffering, and playback delivery for compatible Discord music bots. The bot connects to the node through a client library and sends player operations over Lavalink's REST and WebSocket APIs.

Running Lavalink separately can reduce audio workload inside the Discord bot process and makes the audio backend independently deployable. It does not remove the need to maintain the bot client, source plugins, network path, credentials, or compatible versions.

## Main moving parts

- **Lavalink server:** Java process that manages players and source managers.
- **Client library:** Node.js, Python, or another client that speaks Lavalink's API.
- **Sources/plugins:** Implement search and track loading for supported services.
- **Configuration:** Usually `application.yml` in the process working directory.
- **Network boundary:** Listener address, port, firewall, password, and optional proxy.

## Guide assumptions

These examples target Lavalink v4-style configuration. Plugin configuration names and supported versions can change, so use the plugin's own README for the version you actually install. The example source mix follows the concepts used by the referenced setup repository, but omits its publicly visible password and avoids exposing the listener to the internet by default.

## Before production

Decide whether the node is local to the bot, on the same private network, or intentionally exposed through a proxy. This decision affects bind address, firewall rules, TLS, secrets management, and client connection settings. Read [security hardening](06-security-hardening.md) before deployment.

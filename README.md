# ZorveX Lavalink Setup Handbook

A practical, security-conscious handbook for deploying a Lavalink v4 audio node, configuring plugins, connecting a Discord music bot, and diagnosing common failures.

> **Independent guide:** This handbook is maintained by ZorveX Development. It is not an official Lavalink project and is not affiliated with Lavalink Devs or the maintainers of any plugin mentioned here.

## What is included

- Standalone server installation and first-run setup
- A safer configuration template and production security checklist
- YouTube Source OAuth, PulseLink, and LavaSearch configuration notes
- Client connection examples for Node.js and Python
- Docker Compose and Linux systemd examples
- Reverse proxy, monitoring, updates, and troubleshooting guidance
- Source/configuration matrix based on the public `itsfizys/Lavalink-Setup` repository, with secrets intentionally omitted

## Start here

1. Read [`docs/01-overview.md`](docs/01-overview.md).
2. Install Java using [`docs/02-prerequisites.md`](docs/02-prerequisites.md).
3. Follow [`docs/03-quick-start.md`](docs/03-quick-start.md).
4. Start from [`examples/application.yml`](examples/application.yml), not from a public production config.
5. Review [`docs/06-security-hardening.md`](docs/06-security-hardening.md) before making the node reachable over the internet.

## Important security warning

The referenced public configuration currently contains a hard-coded Lavalink password (`aeroxdevs`) and binds the server to `0.0.0.0` on port `80`. Treat that password as publicly disclosed and do not reuse it. Anyone operating a deployment based on that configuration should rotate the password, inspect access/log history, and verify that only intended network paths can reach the node. This handbook's examples do not reproduce that password.

## Configuration principles

- Pin versions that have been tested together. Do not assume a plugin's newest release is compatible with every Lavalink release.
- Keep credentials and OAuth refresh tokens out of Git, issue reports, screenshots, and logs.
- Prefer loopback or a private network for the Lavalink listener; expose only a deliberate, authenticated route when remote access is required.
- Treat third-party plugins, source adapters, and remote cipher services as separate dependencies that need their own review.
- Verify current syntax and versions against the upstream documentation linked below.

## Official and upstream references

- [Lavalink documentation](https://lavalink.dev/)
- [Lavalink getting started](https://lavalink.dev/getting-started/)
- [Lavalink configuration](https://lavalink.dev/configuration/)
- [Lavalink repository](https://github.com/lavalink-devs/Lavalink)
- [YouTube Source plugin](https://github.com/lavalink-devs/youtube-source)
- [LavaSearch](https://github.com/topi314/LavaSearch)
- [PulseLink](https://github.com/ItzRandom23/PulseLink)
- [Wavelink documentation](https://wavelink.readthedocs.io/)
- [Lavalink client for Node.js](https://github.com/lavalink-devs/Lavalink-Client)

## License and attribution

See [`LICENSE.md`](LICENSE.md). Upstream projects and plugins retain their own licenses and trademarks. This handbook does not repackage the `Lavalink.jar` binary or any third-party plugin artifact.

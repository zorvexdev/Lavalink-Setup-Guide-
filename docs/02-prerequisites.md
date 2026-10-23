# 02 · Prerequisites

## Java runtime

Install a supported Java runtime. The referenced setup targets Java 17 or newer; check the current Lavalink release notes before choosing a runtime for a new production node.

Verify the runtime:

```bash
java -version
```

If the command is missing or shows an older runtime, install or switch to a supported JDK/JRE and open a fresh shell. On Linux, also verify which Java executable the service manager will use, since an interactive shell and systemd can have different environments.

## Host and network

- A Linux x86-64 host is the common deployment target; check upstream hardware support if running ARM or another platform.
- Allow outbound DNS and HTTPS to the upstream services and Maven repositories used by your plugins.
- Keep the Lavalink listening port private unless remote access is deliberate.
- Reserve disk space for rolling logs and enough memory for the server, plugins, and active players.

## Files

You generally need a Lavalink release JAR and an `application.yml` file in the same working directory. Get the JAR from the official Lavalink release page. Avoid executing binaries from random file hosts, and verify release checksums or signatures when upstream publishes them.

## Client compatibility

Choose a maintained client that explicitly supports the Lavalink server version you're deploying. A running node alone does not guarantee that a bot client or plugin is compatible.

# 12 · Docker deployment

Docker can make the Java runtime, filesystem paths, and restart behavior more predictable. Use the official/current image instructions from the [Lavalink documentation](https://lavalink.dev/getting-started/) rather than assuming an image tag is forever current.

## Example Compose file

See [`../examples/compose.yaml`](../examples/compose.yaml). It mounts a local configuration read-only, provides the node password through an environment variable, and does not publish the node to the public host interface by default.

## Before running

- Put `application.yml` in the expected mounted location for the chosen image.
- Set `LAVALINK_SERVER_PASSWORD` in the shell or secret manager.
- Verify the image's documented config path, Java version, and startup command.
- Do not mount a whole home directory into the container.
- Persist logs only if you have a retention policy; ensure they do not contain secrets.
- For a bot in a separate container, put both containers on a private Docker network and use the service name as the node host. Do not publish a public port unless required.

## Upgrade strategy

Pin an image tag or digest, test upgrades in staging, and retain a known-good configuration/image pair for rollback. Avoid automatic upgrades to untested major versions in production.

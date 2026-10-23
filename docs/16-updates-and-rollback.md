# 16 · Updates and rollback

## What to track

- Lavalink server version
- Java runtime version
- Each plugin artifact/version/repository
- Client library version in the bot
- Relevant configuration changes

## Controlled update process

1. Read release notes and compatibility requirements for Lavalink and each plugin.
2. Back up the configuration, excluding live secrets from ordinary archives.
3. Record the working JAR/image and plugin versions.
4. Test in a staging environment with common tracks, searches, playlists, filters, seeking, and reconnection.
5. Upgrade one layer at a time where practical.
6. Monitor logs and error rates after deployment.
7. Roll back the exact version/config combination if startup or playback regresses.

## Snapshot dependencies

Snapshots may change and are not equivalent to stable release artifacts. Keep a precise commit/hash and repository URL, and record when it was tested. Do not switch a dependency to an unverified "latest" value in a production config.

## Rollback

A rollback should restore the previous server binary/image, plugin coordinates, and compatible config together. Restoring only the JAR may not be enough if a plugin dependency also changed.

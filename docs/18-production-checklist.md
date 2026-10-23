# 18 · Production checklist

## Runtime and compatibility

- [ ] Java runtime is supported by the chosen Lavalink release.
- [ ] Client library explicitly supports the deployed Lavalink version.
- [ ] Plugin versions are pinned and tested together.
- [ ] The source/provider matrix is documented and tested.

## Security

- [ ] Unique, high-entropy node password is configured outside version control.
- [ ] Any password previously published in a public repository has been rotated.
- [ ] Listener is private by default or exposed only through a reviewed secure route.
- [ ] Firewall/security-group rules are least-privilege.
- [ ] OAuth refresh tokens and provider credentials are stored as secrets.
- [ ] Request payload logging is disabled unless temporarily required.
- [ ] Metrics/log access is restricted.
- [ ] Remote cipher services and plugins have been reviewed.

## Reliability

- [ ] Process restart or container restart policy is configured.
- [ ] Health monitoring and meaningful alerts exist.
- [ ] A staging update path is available.
- [ ] Previous known-good binary/image and config can be restored.
- [ ] Logs have size and retention limits.
- [ ] Recovery has been tested after a node restart.

## Playback tests

- [ ] Basic track search and playback work.
- [ ] Multiple sources are tested individually.
- [ ] Playlist/album loading works where supported.
- [ ] Pause, resume, seek, volume, and filters are tested.
- [ ] Empty search results and provider failures have user-friendly behavior.
- [ ] Node outage/reconnect does not cause a tight retry loop.

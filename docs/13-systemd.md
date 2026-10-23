# 13 · systemd service on Linux

A systemd unit can start Lavalink at boot, restart it after a crash, and run it under a dedicated low-privilege account.

## Example unit

See [`../examples/lavalink.service`](../examples/lavalink.service). Edit the paths and account names to match the host. Do not run the process as root unless there is a specific, justified reason.

## Suggested deployment layout

- `/opt/lavalink/`: JAR and non-secret configuration
- `/var/lib/lavalink/`: writable application data if needed
- `/var/log/lavalink/` or configured log directory: logs with restricted access
- A protected environment file or systemd credential mechanism for secrets

Avoid setting permissive file modes on environment files. Use `chmod 600` and restrict ownership to the service account or root.

## Commands

```bash
sudo systemctl daemon-reload
sudo systemctl enable --now lavalink
sudo systemctl status lavalink
journalctl -u lavalink -f
```

Review the unit and logs before relying on restart behavior. After changing environment variables or the service file, reload systemd and restart the service.

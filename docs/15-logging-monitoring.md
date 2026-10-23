# 15 · Logging and monitoring

## Logs

Startup logs are often the fastest way to identify missing plugin artifacts, unsupported configuration keys, OAuth initialization errors, and connection failures. Keep the default log level in production unless you need more detail.

Detailed request logs may include payloads and query values. Do not enable them indiscriminately. Redact credentials before sharing diagnostic output.

## Metrics

Lavalink can expose Prometheus metrics when configured. Treat the metrics endpoint as an internal observability endpoint: bind it behind a private interface or restrict it with network controls. Do not publish it openly just because it is read-only.

## Useful operational signals

- Process uptime and unexpected restart count
- Memory and CPU pressure
- Active players and node statistics
- Track load failures and stuck-track events
- Connection/reconnect frequency from bot clients
- Provider-specific error rates and upstream rate limits
- Disk usage and log growth

## Alerting

Alert on persistent node unavailability and repeated failure patterns, not a single failed track from an external provider. Include a runbook link and the current deploy/version identifier in incident notes.

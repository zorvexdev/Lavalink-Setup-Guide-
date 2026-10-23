# 03 · Quick start

## 1. Prepare a directory

```bash
mkdir -p ~/lavalink
cd ~/lavalink
```

Download a supported `Lavalink.jar` release from the official [Lavalink releases](https://github.com/lavalink-devs/Lavalink/releases) page and place it in this directory. Place a reviewed `application.yml` beside it.

## 2. Set configuration

Start with [`../examples/application.yml`](../examples/application.yml). Before first use, provide a unique password via the environment variable `LAVALINK_SERVER_PASSWORD` or your service's secret manager. Do not use a password copied from a public example.

## 3. Start Lavalink

```bash
java -jar Lavalink.jar
```

Keep the terminal open while you watch startup logs. Resolve configuration or plugin-loading errors before connecting a bot.

## 4. Test locally

If the node listens on `127.0.0.1:2333`, test from the same host. Use the API path and headers documented by the current Lavalink API docs. The configured password must match the client password.

Do not paste the password into a public shell transcript or support post. If you must share logs, redact authorization headers, refresh tokens, internal hostnames, and any personally identifying data.

## 5. Connect a client

Use a maintained Lavalink client. Example connection snippets are in [Node.js](10-nodejs-client.md) and [Python](11-python-client.md). They are starting points, not full bot implementations.

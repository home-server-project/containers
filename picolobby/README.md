# PicoLobby

Lightweight Rust Minecraft lobby with player interaction, NPCs, and a server selector.

Upstream: https://github.com/nobuildersnotools/PicoLobby (MIT).

## Image

`ghcr.io/home-server-project/picolobby:stable`

Built from upstream commit `8e952bd0624eb94d9b093f5af19128e32c19bbb2` using its committed `Cargo.lock`. The build uses the upstream Rust 1.96.0 toolchain and ships only the compiled executable and license in a non-root runtime image.

## Configuration

PicoLobby reads `/config/server.toml` (generated on first run). Mount a persistent, writable directory at `/config`. The container listens on TCP port `25565` unless configured otherwise.

For a Velocity network, configure `[forwarding]` with `method = "MODERN"` and the matching forwarding secret; set `[lobby] enabled = true` and configure `[[lobby.servers]]` / `[[lobby.npcs]]` for destinations. Keep the lobby reachable only from the proxy's private network.

Upstream configuration: https://github.com/nobuildersnotools/PicoLobby/blob/master/docs/config/default-configuration.md

Upstream proxy guide: https://github.com/nobuildersnotools/PicoLobby/blob/master/docs/config/proxy-integration.md

The `:stable` image is published by this repository's PicoLobby workflow when changes land on `main`. Upstream revision changes are explicit changes to `picolobby/Containerfile`.

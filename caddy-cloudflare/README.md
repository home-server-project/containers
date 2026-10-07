# Caddy + Cloudflare DNS

Caddy container with the Cloudflare DNS provider module for DNS-01 certificate validation.

## Upstream

The build follows the official Caddy major-version 2 channel:

- builder: `docker.io/library/caddy:2-builder`
- runtime: `docker.io/library/caddy:2`

Docker Hub is the version source of truth. The build does not separately resolve a Caddy release from GitHub.

## Image

`ghcr.io/home-server-project/caddy-cloudflare:stable`

## Cloudflare token

Use a scoped Cloudflare API token for the required zone with:

- `Zone.Zone:Read`
- `Zone.DNS:Edit`

Expose the token to Caddy as `CF_API_TOKEN`.

Example Caddy configuration:

```caddyfile
{
    email you@example.com
    acme_dns cloudflare {env.CF_API_TOKEN}
}
```

## Verify

```bash
podman run --rm --entrypoint caddy   ghcr.io/home-server-project/caddy-cloudflare:stable   list-modules | grep -Fx dns.providers.cloudflare
```

Expected output:

```text
dns.providers.cloudflare
```

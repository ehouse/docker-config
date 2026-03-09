# Self Hosted

Instructions for myself in case I need to reconfigure or re-setup the environment.

## Infrastructure

- **Hardware**: M4 Mac Mini
- **Orchestration**: Komodo (manages all containers)
- **Networking**: Cloudflare Tunnel (`cirno`) for external access, nginx reverse proxy for local HTTPS
- **Local DNS**: `cirno.eeveenet` → Mac Mini local IP
- **Docker Networks**:
  - `komodo_internal` — Komodo-managed containers
  - `cloudflare-tunnel` — Cloudflare tunnel container

## Prerequisites

- Docker Desktop
- Komodo deployed and running
- Local DNS record for `cirno.eeveenet` pointing to Mac Mini
- mkcert installed for local SSL: `brew install mkcert && mkcert -install`

## Configuration

`.env` files are not committed. Required variables:

## Local SSL (mkcert)
```bash
brew install mkcert
mkcert -install
mkcert cirno.eeveenet
```

Place the generated certs in the `internal-proxy/certs/` directory. The CA root for trusting on other devices is at:

## Commands
```bash
docker compose up -d        # start
docker compose down         # stop
docker compose logs -f      # logs
docker compose restart      # restart all
```

## Notes

- FoundryVTT data lives at `/Users/ehouse/Data/foundrydata`
- Komodo is local-only, not exposed via Cloudflare tunnel
- Tunnel token from: `cloudflared tunnel token cirno`
- Cloudflare tunnel managed at: Cloudflare Dashboard → Zero Trust → Networks → Tunnels → cirno
- Resource sync configured to this repo for Komodo state

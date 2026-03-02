# Self Hosted

Instructions for myself in case I need to reconfigure or re-setup the environment

## Prerequisites

- Docker Desktop
- Shared Docker network: `docker network create shared`
- Cloudflare tunnel configured at `foundry.derbynet.io`

## Configuration

`.env` (Not committed)
```
FOUNDRY_USERNAME=
FOUNDRY_PASSWORD=
FOUNDRY_LICENSE_KEY=
TUNNEL_TOKEN=
```

## Commands

```bash
docker compose up -d        # start
docker compose down         # stop
docker compose logs -f      # logs
docker compose restart      # restart all
```

## Notes

- FoundryVTT data lives at `/Users/ehouse/Data/foundrydata`
- Accessible locally at `http://localhost:30000`
- Accessible remotely at `https://foundry.derbynet.io`
- Tunnel token from: `cloudflared tunnel token cirno`
- Cloudflare tunnel managed at: Cloudflare Dashboard → Zero Trust → Networks → Tunnels → cirno

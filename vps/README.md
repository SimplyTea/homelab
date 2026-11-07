# VPS

The remote node. It hosts the media and file services that family and guests use, reached through Tailscale and Cloudflare.

**Specs:** `Shared server with [8GB~ RAM, 4TB Storage]`
**OS:** `[Debian 5.10.226-1]`
**Virtualization:** KVM.

## Services

| Service | Folder | Purpose |
|---------|--------|---------|
| Immich | [`immich/`](immich/README.md) | Photo and video backup |
| Jellyfin | [`jellyfin/`](jellyfin/README.md) | Movies, TV, music, ebooks, audiobooks |
| Ombi | [`ombi/`](ombi/README.md) | Media requests |
| *arr Apps | No Guide, find on Ombi | Filter rules for Ombi |

## Exposure

Services are reached through `[Cloudflare Tunnel / Tailscale only / both]`. Ports published on the host are listed in each service's compose file, and only the ones you need should be open to the internet `[confirm]`.
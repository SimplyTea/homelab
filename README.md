# homelab

This is my home network and remote media server, written up as I build it. A Raspberry Pi at home filters DNS and handles VPN access. A VPS in the cloud serves my photos and media. The Pi also runs [symbolon (privated currently)](https://github.com/SimplyTea/symbolon), my peer-to-peer chat project, as a live test environment.

Nothing here is production-grade. It's a place to learn, break things, and write down how I fixed them.

### Built With

[![Raspberry Pi](https://img.shields.io/badge/Raspberry%20Pi-A22846?style=for-the-badge&logo=raspberrypi&logoColor=white)](https://www.raspberrypi.com/)
[![AdGuard Home](https://img.shields.io/badge/AdGuard%20Home-68BC71?style=for-the-badge&logo=adguard&logoColor=white)](https://adguard.com/en/adguard-home/overview.html)
[![Tailscale](https://img.shields.io/badge/Tailscale-242424?style=for-the-badge&logo=tailscale&logoColor=white)](https://tailscale.com/)
[![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)](https://www.cloudflare.com/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![Jellyfin](https://img.shields.io/badge/Jellyfin-00A4DC?style=for-the-badge&logo=jellyfin&logoColor=white)](https://jellyfin.org/)
[![Immich](https://img.shields.io/badge/Immich-4250AF?style=for-the-badge)](https://immich.app/)
[![Ombi](https://img.shields.io/badge/Ombi-7B2DB3?style=for-the-badge)](https://ombi.io/)

([back to top](#readme-top))

## Features

- [x] DNS that supports Ad and tracker blocking for every device on my network, through AdGuard Home
- [x] Remote access to home services over VPN, without opening ports on my router
- [x] Custom domain routing through Cloudflare
- [x] Self-hosted photo and video backup with Immich
- [x] Media streaming with Jellyfin: movies, TV, music, ebooks, and audiobooks
- [x] Media requests for household members with Ombi
- [x] Live test environment for Nocom on the Pi
- [x] Group-based access control with defined access levels
- [x] Automated backups for Immich and Pi configs
- [ ] Monitoring for the Pi and VPS

## Lab Layout

| Host | Location | Runs |
|------|----------|------|
| Raspberry Pi | Home | Pi-hole, AdGuard Home, Tailscale, Symbolon test node |
| VPS | Remote | Immich, Jellyfin, Ombi |
| Cloudflare | DNS | Domain routing to the Pi and VPS |

**Hardware:** Pi `[model, RAM, storage]`. VPS `[provider, plan, specs]`. Router `[model]`.

## Services

**AdGuard Home** block ads and trackers at the DNS level. AdGuard Home handles filtering, blocklists and query logs.

**Tailscale** is a WireGuard-based VPN that lets my devices reach home services from anywhere. It handles key exchange and NAT traversal for me, and access rules decide which devices can reach which services. Devices on the tailnet get the same DNS filtering as devices at home.

**Symbolon test node (NOT PUBLISHED HERE)** runs on the Pi and my laptop. It discovers peers on the local network, so the Pi works as a real test bench for discovery, group chats, and encryption on my ordinary home network.

**Immich** is my self-hosted photo and video backup.

**Jellyfin** serves movies, TV, music, ebooks, and audiobooks.

**Ombi** lets people in the house request titles, which then appear in Jellyfin.

***arr Apps** Radarr, Prowlarr, Sonarr, Lidarr, Autobrr are all used to help Jellyfin and Ombi with filtering rules. Their configs will not be supplied.

Remote traffic reaches the Pi / VPS through `[Cloudflare Tunnel / direct DNS]`.

## Access

Access is set by role, and each role gets only what it needs. Admins can override any media limit.

| Role | Services | Media limits | Requests |
|------|----------|--------------|----------|
| Admin and family | Jellyfin, Ombi | Up to 4K video, FLAC audio | Auto-approved in Ombi |
| Guest | Jellyfin, Ombi | 1080p video, FLAC audio | `[approval rule]` |

Audio is FLAC for every role. Compressed audio is only used when an admin overrides the setting. Immich only the Admin and Family can see and edit.

Secrets stay in `.env` files that are excluded from version control. No ports are open on my router. Updates are applied automatically every week, unless I see a recent CVE affected a service then I manually update ASAP.


## Roadmap

- [ ] Write up the VPN setup
- [ ] Add Cloudflare notes, with no tokens or account IDs
- [ ] Document access groups and levels
- [ ] Back up Immich and Pi configs
- [ ] Test restores, not just backups
- [ ] Add monitoring for the Pi and VPS
- ...and more planned for this.

See the [open issues](https://github.com/SimplyTea/homelab/issues) for proposed changes and known problems.

([back to top](#readme-top))

## Sharing

This is a personal project, so I'm not looking for contributions, but questions and security concerns are welcome. If you find a security problem, please tell me privately before posting it.

## Credits

The Built With badges, Features checklist, and Roadmap format are based on [othneildrew/Best-README-Template](https://github.com/othneildrew/Best-README-Template). The layout of the overall README is adapted from [khuedoan/homelab](https://github.com/khuedoan/homelab). The content here is my own.
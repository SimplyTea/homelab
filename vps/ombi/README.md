# Ombi

Media requests for household members. Requests appear in Jellyfin once approved.

## Request rules

| Role | Approval | Limits |
|------|----------|--------|
| Admin and family | Auto-approved | Up to 4K video, FLAC audio |
| Guest | `[approval rule]` | 1080p video, FLAC audio |

Audio is FLAC for every role. Compressed audio is only used when an admin overrides the setting.
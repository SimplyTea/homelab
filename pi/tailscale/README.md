# Tailscale

Remote access to the home network and VPS. Tailscale runs WireGuard for the encrypted tunnels and manages keys and NAT traversal for you.


## Setup

1. Install Tailscale on the Pi: `curl -fsSL https://tailscale.com/install.sh | sh`
2. Join the tailnet: `sudo tailscale up --advertise-exit-node=false` `[plus any routes or DNS flags you use]`
3. Approve the device in the admin console, then apply the ACL policy.

## Access rules

See [`acl.example.json`](acl.example.json) and [`../../docs/access-policy.md`](../../docs/access-policy.md).

## Proof to add

- [ ] `tailscale status`, with IPs and names hidden
- [ ] The ACL editor, showing groups and rules, with usernames replaced by placeholders

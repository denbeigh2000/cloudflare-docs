---
_build:
  publishResources: false
  render: never
  list: never
---

Perform these steps in [Zero Trust](https://one.dash.cloudflare.com/).

1. Set your [Split Tunnels mode](/cloudflare-one/connections/connect-devices/warp/configure-warp/route-traffic/split-tunnels/#change-split-tunnels-mode) to **Exclude IPs and domains**.
2. [Add the following entries](/cloudflare-one/connections/connect-devices/warp/configure-warp/route-traffic/split-tunnels/#add-a-route) to your Split Tunnel Exclude list:

    - Private IP address range exposed by your third-party VPN client. For example,
    | Selector | Value |
    | -------- | ----- |
    | IP Address   | `172.16.0.0/12` |
    |
    - Server that your third-party VPN client connects to. For example,
    | Selector | Value |
    | -------- | ----- |
    | Domain   | `*.cvpn-endpoint-xxxxx.prod.clientvpn.us-west-2.amazonaws.com` |

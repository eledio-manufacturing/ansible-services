# Role: vpn

Purpose

Installs OpenVPN and deploys a client configuration. Enables and starts the `openvpn-client@<name>` systemd service.

Variables

| Variable | Required | Default | Description |
|---|---|---|---|
| `vpn_config_content` | yes | — | Full content of the `.ovpn` / `.conf` file |
| `vpn_config_name` | no | `client` | Config name — used as filename and systemd instance name |

Providing the client configuration

- Option A — inline string (encrypt with `ansible-vault`)
- Option B — load from local file in the playbook using `lookup('file', ...)`

Example playbook and details: see roles/vpn/README.md

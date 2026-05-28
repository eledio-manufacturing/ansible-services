# vpn

Installs OpenVPN and deploys a client configuration. Enables and starts
`openvpn-client@<name>` systemd service.

## Variables

| Variable | Required | Default | Description |
|---|---|---|---|
| `vpn_config_content` | yes | — | Full content of the `.ovpn` / `.conf` file |
| `vpn_config_name` | no | `client` | Config name — used as filename and systemd instance name |

## Providing the client configuration

The config is deployed to `/etc/openvpn/client/{{ vpn_config_name }}.conf`.

### Option A — inline string (encrypt with ansible-vault)

```yaml
# group_vars/all/vpn.yml  (encrypt this file with ansible-vault)
vpn_config_content: |
  client
  dev tun
  proto udp
  remote vpn.example.com 1194
  ...
```

### Option B — load from local file in the playbook

```yaml
# playbook.yml
- hosts: all
  vars:
    vpn_config_content: "{{ lookup('file', 'files/client.ovpn') }}"
  roles:
    - eledio.services.vpn
```

### Option C — load and encrypt the file with ansible-vault

```bash
ansible-vault encrypt files/client.ovpn
```

Then reference it:

```yaml
vars:
  vpn_config_content: "{{ lookup('file', 'files/client.ovpn') }}"
```

## Example playbook

```yaml
- hosts: raspberries
  become: true
  vars:
    vpn_config_name: home
    vpn_config_content: "{{ lookup('file', 'files/home.ovpn') }}"
  roles:
    - eledio.services.vpn
```

This deploys `/etc/openvpn/client/home.conf` and manages `openvpn-client@home`.

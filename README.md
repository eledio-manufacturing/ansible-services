# Ansible Collection - eledio.services

Collection of roles for deploying and managing services on Debian-based systems
(including Raspberry Pi OS).

## Roles

| Role | Description |
|---|---|
| `eledio.services.install_uv` | Install [uv](https://github.com/astral-sh/uv) Python package manager system-wide |
| `eledio.services.vpn` | Install OpenVPN and deploy client configuration |

## Installation

### From local path (development)

```yaml
# requirements.yml
collections:
  - name: /path/to/ansible-collection-eledio-services
    type: dir
```

```bash
ansible-galaxy collection install -r requirements.yml
```

### From GitHub

```yaml
# requirements.yml
collections:
  - name: https://github.com/eledio-manufacturing/ansible-services.git
    type: git
    version: main
```

```bash
ansible-galaxy collection install -r requirements.yml
```

### From tarball

```bash
ansible-galaxy collection build
ansible-galaxy collection install eledio-services-*.tar.gz
```

## Usage

```yaml
- hosts: raspberries
  become: true
  roles:
    - eledio.services.install_uv
    - eledio.services.vpn
```

## Role variables

### install_uv

| Variable | Default | Description |
|---|---|---|
| `uv_install_dir` | `/usr/local/bin` | Directory to install uv binary into |

### vpn

| Variable | Required | Default | Description |
|---|---|---|---|
| `vpn_config_content` | yes | — | Full content of the `.ovpn` / `.conf` file |
| `vpn_config_name` | no | `client` | Config name — filename and systemd instance name |

See `roles/vpn/README.md` for full documentation on supplying the VPN config.

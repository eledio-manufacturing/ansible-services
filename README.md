# Ansible Collection - eledio.services

Collection of roles for deploying and managing services on Debian-based systems
(including Raspberry Pi OS).

## Roles

| Role | Description |
|---|---|
| `eledio.services.common` | Base system setup — apt update and essential packages |
| `eledio.services.install_uv` | Install [uv](https://github.com/astral-sh/uv) Python package manager system-wide |
| `eledio.services.vpn` | Install OpenVPN and deploy client configuration |
| `eledio.services.st_link` | Deploy ST-Link udev rules for USB access |
| `eledio.services.label_printer` | Deploy and run the label printer service (printer-tsc) |

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
    - eledio.services.common
    - eledio.services.install_uv
    - eledio.services.vpn
```

## Role variables

### common

| Variable | Default | Description |
|---|---|---|
| `common_packages` | see defaults | List of apt packages to install — extend per playbook |

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

### st_link

No variables. Deploys `/etc/udev/rules.d/99-stlink.rules` and reloads udev.

### label_printer

| Variable | Required | Default | Description |
|---|---|---|---|
| `label_printer_git_user` | yes | — | GitHub username for cloning printer-tsc |
| `label_printer_git_token` | yes | — | GitHub token for cloning printer-tsc (use ansible-vault) |
| `label_printer_config_content` | yes | — | Full content of `config/config.yaml` (use ansible-vault) |
| `label_printer_install_dir` | no | `/srv/printer` | Service installation directory |
| `label_printer_user` | no | `pi` | OS user that owns and runs the service |

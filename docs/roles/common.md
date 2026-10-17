# Role: common

Purpose

Base system setup. Updates apt cache and installs essential packages. Run this role first in any playbook.

Optionally also bootstraps a freshly imaged host: full dist-upgrade, hostname, and authorized SSH keys. All of these are off by default.

Variables

| Variable | Default | Description |
|---|---|---|
| `common_packages` | See defaults | List of apt packages to install |
| `common_show_host_facts` | `true` | Print hostname, IP, distro and kernel at the start of the role |
| `common_upgrade_packages` | `false` | Run a full `apt dist-upgrade` |
| `common_hostname` | `""` | Hostname to set (empty = leave as is). Also removes the stale `127.0.1.1` line from `/etc/hosts` |
| `common_ssh_user` | `ansible_user`, else `pi` | Account to add `common_authorized_keys` to |
| `common_authorized_keys` | `[]` | SSH public keys to authorize for `common_ssh_user` (uses `ansible.posix.authorized_key`) |

Defaults file: roles/common/defaults/main.yml

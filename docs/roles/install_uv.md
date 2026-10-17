# Role: install_uv

Purpose

Installs the `uv` Python package manager system-wide. The role skips installation when the `uv` binary is already present, unless it is older than `install_uv_min_version`.

Variables

| Variable | Default | Description |
|---|---|---|
| `install_uv_install_dir` | `/usr/local/bin` | Directory to install the `uv` binary into |
| `install_uv_min_version` | `""` | Upgrade an installed `uv` older than this (e.g. `"0.5.0"`). Empty = never upgrade an existing binary |

Defaults file: roles/install_uv/defaults/main.yml

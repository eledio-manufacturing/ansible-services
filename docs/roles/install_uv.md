# Role: install_uv

Purpose

Installs the `uv` Python package manager system-wide. The role skips installation when the `uv` binary is already present.

Variables

| Variable | Default | Description |
|---|---|---|
| `install_uv_install_dir` | `/usr/local/bin` | Directory to install the `uv` binary into |

Defaults file: roles/install_uv/defaults/main.yml

# install_uv

Installs [uv](https://github.com/astral-sh/uv) Python package manager system-wide.
Skips install if binary already present, unless it's older than
`install_uv_min_version`.

## Variables

| Variable | Default | Description |
|---|---|---|
| `install_uv_install_dir` | `/usr/local/bin` | Directory to install uv binary into |
| `install_uv_min_version` | `""` | Upgrade an installed uv older than this (e.g. `"0.5.0"`). Empty = never upgrade an existing binary |

Set `install_uv_min_version` when deploying a project with a `uv.lock`: a
lockfile written by a newer uv can't be read by an older one, so an old
binary left on the host would otherwise break `uv sync`.

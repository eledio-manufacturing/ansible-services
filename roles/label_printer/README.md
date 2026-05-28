# label_printer

Clones the printer-tsc service, syncs Python dependencies via uv,
deploys station config and systemd service unit.

## Variables

| Variable | Required | Default | Description |
|---|---|---|---|
| `label_printer_git_user` | yes | — | GitHub username for cloning printer-tsc |
| `label_printer_git_token` | yes | — | GitHub token (use ansible-vault) |
| `label_printer_config_content` | yes | — | Full content of `config/config.yaml` (use ansible-vault) |
| `label_printer_install_dir` | no | `/srv/printer` | Service installation directory |
| `label_printer_user` | no | `pi` | OS user that owns and runs the service |

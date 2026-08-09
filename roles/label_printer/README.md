# label_printer

Clones the printer-tsc service, syncs Python dependencies via uv,
deploys station config and systemd service unit.

## Variables

| Variable | Required | Default | Description |
|---|---|---|---|
| `label_printer_config_content` | yes | — | Full content of `config/config.yaml` (use ansible-vault) |
| `label_printer_install_dir` | no | `/srv/printer` | Service installation directory |
| `label_printer_user` | no | `pi` | OS user that owns and runs the service |
| `label_printer_log_dir` | no | `/var/log/printer-tsc` | Log directory, precreated and owned by `label_printer_user`. Point `logging.path` in `config.yaml` here to enable rotating file logging. |

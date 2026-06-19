# Usage

Example playbook using multiple roles from this collection:

```yaml
- hosts: raspberries
  become: true
  roles:
    - name: eledio.services.common
    - name: eledio.services.install_uv
    - name: eledio.services.label_printer
      vars:
        label_printer_config_content: "{{ lookup('file', 'files/printer-config.yaml') }}"
    - name: eledio.services.vpn
      vars:
        vpn_config_name: home
        vpn_config_content: "{{ lookup('file', 'files/home.ovpn') }}"
```

Notes:

- Sensitive contents (service configs, VPN client files) should be stored and encrypted with `ansible-vault` when appropriate.
- Role variables and defaults are documented on each role page.

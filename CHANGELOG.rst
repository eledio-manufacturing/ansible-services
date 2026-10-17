================================
eledio.services Change Log
================================

Unreleased
----------

Changes
-------
- common: optional host bootstrap, all off by default — ``common_upgrade_packages`` (full dist-upgrade), ``common_hostname`` (also drops the stale ``127.0.1.1`` line from ``/etc/hosts``) and ``common_authorized_keys`` / ``common_ssh_user``. Prints host facts at the start (``common_show_host_facts``, default on).
- install_uv: ``install_uv_min_version`` upgrades an installed uv older than the given version. Empty (default) keeps the old behaviour of never touching an existing binary.
- Add ``ansible.posix`` (>=1.5.0) as a collection dependency, for ``common_authorized_keys``.


v1.1.7
======

Release Summary
---------------
Fix USB conflict between ipp-usb and Brother QL label printer.

Changes
-------
- label_printer: mask ``ipp-usb`` service to prevent it from claiming the Brother QL USB device and causing "Resource busy" errors.


v1.1.6
======

Release Summary
---------------
Precreate the label printer log directory for optional rotating file logging.

Changes
-------
- label_printer: precreate ``label_printer_log_dir`` (default ``/var/log/printer-tsc``), owned by ``label_printer_user``, for optional rotating file logging.


v1.1.4
======

Release Summary
---------------
Improve GitHub issue templates.

Changes
-------
- Update GitHub issue templates.


v1.1.2
======

Release Summary
---------------
Documentation and CI deployment improvements.

Changes
-------
- Add MkDocs-based documentation site with per-role pages and contributing guide.
- Add GitHub Actions workflow to build and deploy the documentation site to GitHub Pages.


v1.1.1
======

Release Summary
---------------
Patch release with metadata namespace fix.

Changes
-------
- Update Galaxy namespace from ``eledio_admin`` to ``eledio``.


v1.1.0
======

Release Summary
---------------
Fix for USB printer access in the `label_printer` role.

Changes
-------
- Add service user to ``lp`` group for USB printer access in ``label_printer`` role.


v1.0.0
======

Release Summary
---------------
Initial release.

New Roles
---------
- ``common`` - Base system setup, apt update and essential packages
- ``install_uv`` - Install uv Python package manager system-wide
- ``vpn`` - Install OpenVPN and deploy client configuration
- ``st_link`` - Deploy ST-Link udev rules for USB access
- ``label_printer`` - Deploy and run the label printer service

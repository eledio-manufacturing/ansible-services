# Contributing

Thanks for considering contributions. Suggested workflow:

1. Fork the repository and create a feature branch.
2. Make changes and add documentation where appropriate (docs/).
3. Update `CHANGELOG.rst` with the user-visible summary of changes.
4. Open a pull request against `main` and describe the change.

Testing

- For collection code changes, run `ansible-lint` and any role-specific molecule tests if present.
- To preview the documentation locally, install MkDocs and build the site:

```bash
pip install mkdocs mkdocs-material
mkdocs serve
```

Publishing the collection to Ansible Galaxy

Build and publish steps for maintainers:

```bash
ansible-galaxy collection build
ansible-galaxy collection publish eledio-services-<version>.tar.gz
```

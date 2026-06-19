# Installation

There are two common ways to install the collection for consumption in playbooks.

1) Install from GitHub (useful for development or pinned commits):

```bash
# Install collection from a local path (developer)
ansible-galaxy collection install /path/to/ansible-services

# Or install directly from a git archive (example)
ansible-galaxy collection install https://github.com/eledio-manufacturing/ansible-services/archive/main.tar.gz
```

2) Build and install locally (building a distributable collection):

```bash
pip install --user ansible-core
ansible-galaxy collection build
ansible-galaxy collection install ./eledio-services-*.tar.gz
```

After installing, use roles in playbooks by their fully qualified collection name, for example `eledio.services.common`.

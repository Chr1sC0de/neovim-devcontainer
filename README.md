# Sample Devcontainer for Neovim

run the following commands

```bash
devcontainer build --workspace-folder . --docker-path podman --log-level debug
devcontainer up --workspace-folder . --docker-path podman --log-level debug
devcontainer exec --workspace-folder . --docker-path podman bash

# to kill and remove
podman kill --all
podman rm --all
```


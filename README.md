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

devcontainer-start.sh

```bash
#!/usr/bin/env bash

podman run -itd \
  --name chris-devcontainer \
  --userns=keep-id:uid=1000 \
  --mount type=bind,source="${HOME}/.config/nvim",target="/home/ubuntu/.config/nvim",rw \
  --mount type=bind,source="$(pwd)",target="/home/ubuntu/workspace",rw \
  -w /home/ubuntu/workspace \
  --replace \
  localhost/chris-devcontainer
```


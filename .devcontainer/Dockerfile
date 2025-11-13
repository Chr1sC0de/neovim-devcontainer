FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    passwd \
    ca-certificates \
    git \
    curl \
    unzip \
    nodejs \
    npm \
    yarn \
    ripgrep \
    fd-find \
    build-essential \
    cmake \
    gettext \
    libtool \
    libtool-bin \
    pkg-config \
    python3 \
    python3-pip \
    python3-venv \
    sudo \
    && rm -rf /var/lib/apt/lists/*


RUN echo "ubuntu ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

USER ubuntu
WORKDIR /home/ubuntu

RUN curl -LO https://github.com/neovim/neovim/releases/latest/download/nvim-linux-x86_64.tar.gz && \ 
    sudo rm -rf /opt/nvim-linux-x86_64 && \ 
    sudo tar --no-same-owner --no-same-permissions -C /opt -xzf nvim-linux-x86_64.tar.gz 

RUN mkdir -p ~/.config/nvim

RUN curl https://sh.rustup.rs -sSf | sh -s -- -y 

RUN curl -LsSf https://astral.sh/uv/install.sh | sh

ENV PATH="$PATH:/opt/nvim-linux-x86_64/bin:/home/ubuntu/.cargo/bin:/home/ubuntu/.local/bin/"

RUN cargo install grip-grab

RUN ln -s $(which fdfind) ~/.local/bin/fd

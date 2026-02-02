FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04
RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    stow \
    git \
    ca-certificates \
    build-essential \
    pkg-config \
    zsh \
    fzf \
    iptables \
    ipset \
    iproute2 \
    dnsutils \
 && rm -rf /var/lib/apt/lists/*
COPY --from=jdxcode/mise /usr/local/bin/mise /usr/local/bin/
RUN echo 'eval "$(mise activate bash)"' >> /home/vscode/.bashrc \
 && echo 'eval "$(mise activate zsh)"'  >> /home/vscode/.zshrc

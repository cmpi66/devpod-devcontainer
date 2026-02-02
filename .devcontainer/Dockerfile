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
    pip \
    zoxide \
    eza \
 && rm -rf /var/lib/apt/lists/*
COPY --from=jdxcode/mise /usr/local/bin/mise /usr/local/bin/
RUN mkdir -p /etc/zsh && \
    echo 'export ZDOTDIR="$HOME/.config/zsh"' > /etc/zsh/zshenv
# Copy your setup script INTO the image (stable location)
COPY scripts/setup /usr/local/bin/devcontainer-setup
RUN chmod +x /usr/local/bin/devcontainer-setup
RUN echo 'eval "$(mise activate bash)"' >> /home/vscode/.bashrc \
 && echo 'eval "$(mise activate zsh)"'  >> /home/vscode/.zshrc

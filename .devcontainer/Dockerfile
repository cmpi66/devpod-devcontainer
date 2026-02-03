FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    stow git ca-certificates \
    build-essential pkg-config \
    zsh fzf \
    iptables ipset iproute2 dnsutils \
    zoxide eza \
    curl unzip xz-utils zip jq \
    python3-pip python3-venv \
 && rm -rf /var/lib/apt/lists/*

COPY --from=jdxcode/mise /usr/local/bin/mise /usr/local/bin/

# System-wide ZDOTDIR (you already want this)
RUN mkdir -p /etc/zsh \
 && printf '%s\n' 'export ZDOTDIR="$HOME/.config/zsh"' > /etc/zsh/zshenv

COPY scripts/setup /usr/local/bin/devcontainer-setup
RUN chmod +x /usr/local/bin/devcontainer-setup
RUN echo 'eval "$(mise activate bash)"' >> /home/vscode/.bashrc \
 && echo 'eval "$(mise activate zsh)"'  >> /home/vscode/.zshrc


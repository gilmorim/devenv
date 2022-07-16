FROM archlinux:base-devel

ARG USERNAME=ggm
ARG USER_HOME=/home/${USERNAME}
ARG ZPLUG_HOME=/home/${USERNAME}

RUN /usr/sbin/bash -c "pacman -Syu --noconfirm" && \
    pacman -S git --noconfirm && \
    pacman -S zsh --noconfirm && \
    useradd -m -s /usr/sbin/zsh $USERNAME && \
    pacman -Sc

USER $USERNAME
WORKDIR $USER_HOME

RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y && \
    source "$HOME/.cargo/env"
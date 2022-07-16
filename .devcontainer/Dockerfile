FROM archlinux:base-devel

ARG USERNAME=ggm
ARG USER_HOME=/home/${USERNAME}

RUN /usr/sbin/bash -c "pacman -Syu --noconfirm" && \
    pacman -S git --noconfirm && \
    pacman -S wget --noconfirm && \
    pacman -S zsh --noconfirm && \
    useradd -m -s /usr/sbin/zsh ${USERNAME} && \
    pacman -Sc

USER $USERNAME
WORKDIR $USER_HOME

RUN wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh || true
RUN git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k

COPY --chown=${USERNAME}:${USERNAME} .devcontainer/resources/sample-zshrc $USER_HOME/.zshrc
COPY --chown=${USERNAME}:${USERNAME} .devcontainer/resources/sample-zshenv $USER_HOME/.zshenv
COPY --chown=${USERNAME}:${USERNAME} .devcontainer/resources/sample-p10k-zsh $USER_HOME/.p10k.zsh

# RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y --no-modify-path && \
#    source "$HOME/.cargo/env"
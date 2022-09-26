FROM gitpod/workspace-base:2022-09-26-11-35-42

USER root
RUN useradd -m -s /bin/bash linuxbrew && \
    usermod -aG sudo linuxbrew &&  \
    mkdir -p /home/linuxbrew/.linuxbrew && \
    chown -R linuxbrew: /home/linuxbrew/.linuxbrew && \
    chown -R linuxbrew: /home/gitpod && \
    chown -R gitpod /home/linuxbrew/.linuxbrew

USER linuxbrew
RUN /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install.sh)"

ENV PATH="/home/linuxbrew/.linuxbrew/bin:${PATH}"

USER gitpod
RUN brew install \
    helm \
    norwoodj/tap/helm-docs \
    pre-commit \
    kubectl

RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" "" --unattended
COPY template.zshrc $HOME/.zshrc

CMD [ "zsh" ]
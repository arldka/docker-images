FROM gitpod/workspace-base:2022-09-26-11-35-42

ENV HELM_VERSION=3.10.0
ENV HELM_DOCS_VERSION=1.11.0
ENV KUBE_VERSION=v1.25.2

USER root

# Install Helm
RUN curl -sSL -o /tmp/helm.tar.gz "https://get.helm.sh/helm-v${HELM_VERSION}-linux-amd64.tar.gz" \
    && tar xvf /tmp/helm.tar.gz -C /tmp \
    && mv /tmp/linux-amd64/helm /usr/local/bin

# Install Helm-Docs
RUN curl -sSL -o /tmp/helm-docs.tar.gz "https://github.com/norwoodj/helm-docs/releases/download/v${HELM_DOCS_VERSION}/helm-docs_${HELM_DOCS_VERSION}_Linux_x86_64.tar.gz" \
    && tar xvf /tmp/helm-docs.tar.gz -C /tmp\
    && mv /tmp/helm-docs /usr/local/bin

# Install Kubectl
RUN curl -OL "https://dl.k8s.io/release/${KUBE_VERSION}/bin/linux/amd64/kubectl" \
    && chmod +x kubectl \
    && mv kubectl /usr/local/bin

USER gitpod

# Install ZSH
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" "" --unattended
COPY template.zshrc $HOME/.zshrc

CMD [ "zsh" ]
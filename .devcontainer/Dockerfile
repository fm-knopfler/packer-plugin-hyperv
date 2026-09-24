FROM mcr.microsoft.com/devcontainers/go:2-1.27

ENV HTTP_PROXY=${HTTP_PROXY} HTTPS_PROXY=${HTTPS_PROXY} NO_PROXY=${NO_PROXY} \
    http_proxy=${HTTP_PROXY} https_proxy=${HTTPS_PROXY} no_proxy=${NO_PROXY}

ARG CA_CERT_SOURCE
ADD ${CA_CERT_SOURCE} /usr/local/share/ca-certificates/corporate-ca.crt

RUN update-ca-certificates
ENV NODE_EXTRA_CA_CERTS=/etc/ssl/certs/ca-certificates.crt
ENV SSL_CERT_FILE=/etc/ssl/certs/ca-certificates.crt

ARG PACKER_VERSION=1.16.0
RUN curl -fsSL https://releases.hashicorp.com/packer/${PACKER_VERSION}/packer_${PACKER_VERSION}_linux_amd64.zip -o /tmp/packer.zip \
    && unzip -q /tmp/packer.zip -d /usr/local/bin \
    && rm /tmp/packer.zip

WORKDIR /workspace
 
CMD ["/bin/bash"]
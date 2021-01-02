FROM jenkins/jnlp-slave:alpine

USER root

ENV HELM_VERSION v3.3.0
ENV HELM_FILENAME helm-${HELM_VERSION}-linux-amd64.tar.gz

RUN apk add --update -t deps curl tar gzip ca-certificates git

RUN curl -L https://get.helm.sh/${HELM_FILENAME} | tar zxv -C /tmp \
  && cp /tmp/linux-amd64/helm /usr/local/bin/helm \
  && chmod +x /usr/local/bin/helm

RUN curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl" -o /usr/local/bin/kubectl \
  && chmod +x /usr/local/bin/kubectl

RUN apk add docker

RUN apk del --purge deps

ENTRYPOINT ["jenkins-slave"]

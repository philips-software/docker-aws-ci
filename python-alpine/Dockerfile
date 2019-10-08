FROM python:3.7-alpine
MAINTAINER Forest Keepers <niek.palm@philips.com>



RUN apk add --update \
  curl \
  jq \
  git \
  bash \
  zip \
  openssl \
  && rm -rf /var/cache/apk/*

ADD REPO .
ADD TAGS .

ENV AWS_CLI_VERSION=1.16.250
ENV KUBECTL_VERSION=v1.16.1

RUN pip install --no-cache-dir --upgrade awscli==${AWS_CLI_VERSION}
RUN wget -q https://storage.googleapis.com/kubernetes-release/release/${KUBECTL_VERSION}/bin/linux/amd64/kubectl -O kubectl
RUN chmod +x ./kubectl && mv ./kubectl /usr/local/bin/kubectl
RUN mkdir -p ~/.kube

CMD ["/bin/bash"]

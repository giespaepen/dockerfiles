FROM ubuntu:latest
LABEL maintainer="gie.spaepen@rombit.be"

RUN apt-get update && \
    apt-get -y -q install software-properties-common && \
    apt-add-repository ppa:ansible/ansible && \
    apt-get -q update && \
    apt-get -y -q install ansible && \
    apt-get -y -q install curl && \
    apt-get -y -q install git && \
    apt-get -y -q install apt-transport-https && \
    apt-get -y -q install sshpass && \
    curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - && \
    echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list && \
    apt-get -q update && apt-get -y -q install yarn && \
    curl -sL https://deb.nodesource.com/setup_8.x | bash - && \
    apt-get install -y nodejs && \
    ansible-playbook --version && \
    yarn --version

WORKDIR /build

ENTRYPOINT [ "node" ]

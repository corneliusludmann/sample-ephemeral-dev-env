FROM gitpod/openvscode-server:latest

# INSTALL REQUIREMENTS
USER root
# node
RUN apt update && apt install -y \
        curl \
    && curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash - \
    && apt update && apt install -y \
        nodejs \
    && rm -rf /var/lib/apt/lists/*
# mongodb
RUN curl -fsSL https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add - \
    && echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/5.0 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-5.0.list \
    && apt update && DEBIAN_FRONTEND=noninteractive apt install -y \
        mongodb-org \
    && rm -rf /var/lib/apt/lists/* \
    && mkdir -p /data/db \
    && chown openvscode-server -R /data/db

USER openvscode-server

# CLONE REPO
RUN git clone https://github.com/gitpod-io/template-typescript-node.git /home/workspace/project && \
    cd /home/workspace/project && \
    git checkout 91ef21d1e7e39bf7db34e2680cb7e74ce50f63b9

# PREBUILD
RUN cd ./project && npm install && npm run build

# START APP
# $ mongod
# $ PORT=8080 npm run start

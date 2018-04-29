# use ubuntu:xenial instead of alpine/debian because they both have a bug with hera+evm2wasm.js (C mktemp function broken)
FROM ubuntu:xenial

RUN apt update -y && apt install -y \
        git \
        cmake \
        g++ \
        make \
        libleveldb-dev libsnappy-dev \
        curl \
        sudo

RUN curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash - && \
    apt install -y \
        nodejs \
        bash jq bc \
        python3 \
        python

RUN apt install wget -y


RUN adduser --disabled-password --gecos '' builder && adduser builder sudo && printf 'builder\tALL=NOPASSWD: ALL\n' >> /etc/sudoers

RUN wget https://dl.google.com/go/go1.10.1.linux-amd64.tar.gz && \
    tar -xzf go1.10.1.linux-amd64.tar.gz go && \
    printf '\nexport PATH=$PATH:/go/bin\nexport GOPATH=/home/builder/go' >> /home/builder/.bashrc

RUN mkdir /home/builder/go

USER builder
WORKDIR /home/builder

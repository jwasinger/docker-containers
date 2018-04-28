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

RUN adduser --disabled-password --gecos '' builder && adduser builder sudo && printf 'builder\tALL=NOPASSWD: ALL\n' >> /etc/sudoers

USER builder
WORKDIR /home/builder


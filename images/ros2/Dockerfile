FROM ros:humble

RUN apt update && apt install curl
RUN curl -L https://go.dev/dl/go1.21.4.linux-amd64.tar.gz | tar -C /usr/local -xzf -
ENV PATH=/usr/local/go/bin:/root/go/bin:$PATH
RUN go install github.com/tiiuae/rclgo/cmd/...@latest
RUN mkdir /work

ARG UID
ARG GID

ENV USER=user \
    GROUP=user \
    HOME=/home/user

RUN groupadd $GROUP -g ${GID:-1000} && \
    useradd -g $GROUP -G sudo -u ${UID:-1000} -m -s /bin/bash $USER && \
    echo 'user:password' | chpasswd && \
    echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

USER $USER
WORKDIR $HOME

FROM golang:1.10

ARG GIT_URL=https://github.com/jp-taku2/isucon8.git
RUN apt update -y && apt install -y git ssh && \
    mkdir /root/.ssh && chmod 700 /root/.ssh && \
    ssh-keyscan github.com >> /root/.ssh/known_hosts && \
    git clone -b local-docker $GIT_URL /home/isucon/torb
WORKDIR /home/isucon/torb/webapp/go
RUN make
EXPOSE 8080

ENTRYPOINT ["/home/isucon/torb/webapp/go/torb"]

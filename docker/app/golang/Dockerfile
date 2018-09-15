FROM golang:1.11

ARG GIT_URL=https://github.com/isucon/isucon7-qualify.git
ADD id_isucon /root/.ssh/id_rsa
ADD id_isucon /home/isucon/.ssh/id_rsa
ADD id_isucon.pub /root/.ssh/id_rsa.pub
ADD id_isucon.pub /home/isucon/.ssh/id_rsa.pub
RUN chmod 600 /home/isucon/.ssh/id_rsa.pub && \
    chmod 600 /root/.ssh/id_rsa && \
    chmod 644 /home/isucon/.ssh/id_rsa.pub && \
    chmod 644 /root/.ssh/id_rsa.pub && \
    ssh-keyscan github.com >> /root/.ssh/known_hosts && \
    echo ls /home/isucon/isubata/
RUN git clone $GIT_URL /home/isucon/isubata
WORKDIR /home/isucon/isubata/webapp/go
RUN make
EXPOSE 5000

ENTRYPOINT ["/home/isucon/isubata/webapp/go/isubata"]

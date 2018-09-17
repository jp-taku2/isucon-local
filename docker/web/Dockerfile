FROM lkwg82/h2o-http2-server
ARG GIT_URL=https://github.com/jp-taku2/isucon8.git
RUN apk update && apk add -U openssh git  && \
    mkdir /root/.ssh && chmod 700 /root/.ssh && \
    ssh-keyscan github.com >> /root/.ssh/known_hosts && \
    git clone -b local-docker $GIT_URL /home/isucon/torb && \
    mkdir -p /var/log/h2o && mkdir -p /var/run/h2o/
EXPOSE 80
COPY /default-h2o.conf /etc/h2o/h2o.conf

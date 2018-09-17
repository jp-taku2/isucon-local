FROM mariadb:5.5

ENV MYSQL_ALLOW_EMPTY_PASSWORD=yes MYSQL_DATABASE=torb MYSQL_USER=isucon MYSQL_PASSWORD=isucon
ARG GIT_URL=https://github.com/jp-taku2/isucon8.git
RUN apt update -y && apt install -y git ssh && \
    mkdir /root/.ssh && chmod 700 /root/.ssh && \
    ssh-keyscan github.com >> /root/.ssh/known_hosts && \
    git clone -b local-docker $GIT_URL /home/isucon/torb
RUN cp /home/isucon/torb/db/schema.sql /docker-entrypoint-initdb.d/01_torb.sql &&\
    cp /home/isucon/torb/db/isucon8q-initial-dataset.sql.gz /docker-entrypoint-initdb.d/isucon8q-initial-dataset.sql.gz 

EXPOSE 3306
CMD ["--character-set-server=utf8mb4"]

FROM mariadb:10.4

RUN apt-get update \
 && apt-get install --no-install-recommends -y tzdata \
 && apt-get clean \
 && rm -r /var/lib/apt/lists/*
COPY custom-my.cnf etc/mysql/conf.d/

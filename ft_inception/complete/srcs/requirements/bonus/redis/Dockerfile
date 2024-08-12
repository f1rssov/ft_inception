FROM debian:buster

RUN apt-get update\
		&& apt-get install -y --no-install-recommends redis procps \
		&& rm -rf /var/lib/apt/lists/*

COPY ./requirements/bonus/redis/conf/redis.conf /etc/redis.conf
#EXPOSE 6379
CMD [ "redis-server", "/etc/redis.conf" ]

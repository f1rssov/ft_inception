FROM debian:buster
RUN apt update && apt install -y \
        --no-install-recommends \
        nginx openssl procps\
        && openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
	-keyout /etc/ssl/private/nginx-selfsigned.key \
	-out /etc/ssl/certs/nginx-selfsigned.crt \
	-subj "/C=RU/ST=RF/L=Moscow/O=42school/OU=dcompreh/CN=localhost/emailAddress=dcompreh@42.fr" \
        && rm -rf /var/lib/apt/lists/* 

COPY ./requirements/nginx/conf/dcompreh.42.fr /etc/nginx/sites-available/
RUN ln -s /etc/nginx/sites-available/dcompreh.42.fr /etc/nginx/sites-enabled/dcompreh.42.fr
RUN rm /etc/nginx/sites-enabled/default && rm /etc/nginx/sites-available/default

EXPOSE 443

ENTRYPOINT ["nginx", "-g", "daemon off;"]


FROM debian:buster

RUN apt update && apt install -y --no-install-recommends \
        procps nodejs &&\
        rm -rf /var/lib/apt/lists/*

COPY ./requirements/bonus/website/tools/ /

ENTRYPOINT [ "node", "site.js" ]

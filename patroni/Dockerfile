FROM postgres:16
ARG version=4.0.2
RUN apt-get update \
    && apt-get install --no-install-recommends python3 python3-pip gosu -y \
    && apt-get clean && rm -rf /var/lib/apt/lists/* \
    && pip3 install --break-system-packages --no-cache patroni==${version} patroni[consul] psycopg2-binary

COPY entrypoint.sh /entrypoint.sh

USER root

ENV DATA_DIR=/data CERTS_DIR=
VOLUME /data

ENTRYPOINT ["/entrypoint.sh"]
CMD ["--help"]

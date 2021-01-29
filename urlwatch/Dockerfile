FROM python:3-alpine

RUN set -xe \
    && apk add --no-cache ca-certificates \
                          build-base      \
                          libffi-dev      \
                          libxml2         \
                          libxml2-dev     \
                          libxslt         \
                          libxslt-dev     \
                          openssl-dev     \
    && pip3 install appdirs   \
                    cssselect \
                    keyring   \
                    lxml      \
                    minidb    \
                    pyyaml    \
                    requests  \
                    chump     \
                    urlwatch  \
    && apk del build-base  \
               libffi-dev  \
               libxml2-dev \
               libxslt-dev \
               openssl-dev \
    && echo '*/30 * * * * cd /root/.urlwatch && urlwatch --urls urls.yaml --config urlwatch.yaml --hooks hooks.py --cache cache.db' | crontab -

VOLUME /root/.urlwatch
WORKDIR /root/.urlwatch

CMD ["crond", "-f", "-L", "/dev/stdout"]

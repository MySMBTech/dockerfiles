# Last modified: Wed, 14 Jul 2021 14:07:23 +0000
FROM python:3.9.6-alpine3.14

# Upgrade all packages to latest
RUN apk --update --no-cache upgrade

COPY requirements.txt .

COPY localtime /etc/localtime

RUN apk --update add --no-cache --virtual .build-dependencies python3-dev build-base wget \
  && pip install --no-cache-dir -r requirements.txt \
  && apk del .build-dependencies

RUN addgroup -g 4000 demisto \
  && adduser -u 4000 -G demisto -D demisto -s /bin/sh 

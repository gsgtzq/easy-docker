FROM python:3-alpine
LABEL MAINTAINER="zhangqi gsgtzq@gmail.com"
RUN apk update \
    && apk add gcc openssl-dev libffi-dev musl-dev python3-dev \
    && pip install mycli \
    && apk del gcc openssl-dev libffi-dev musl-dev python3-dev \
    && rm /var/cache/*
ENTRYPOINT [ "mycli" ]
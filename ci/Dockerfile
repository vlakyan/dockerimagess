FROM docker:latest

MAINTAINER Vitaly Losev <vitaly.losev93@gmail.com>

RUN apk add --no-cache \
    py-pip \
    python-dev \
    libffi-dev \
    openssl-dev \
    gcc \
    libc-dev \
    make \
    curl \
    bash

RUN pip install docker-compose
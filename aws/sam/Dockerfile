FROM python:3.8.0-alpine3.10

RUN apk update \
    && apk upgrade \
    && apk add --no-cache --virtual build-deps build-base gcc \
    && pip install --upgrade pip \
    && pip install awscli \
    && pip install aws-sam-cli \
    && apk del build-deps

ENV SAM_CLI_TELEMETRY=0

RUN mkdir /work

WORKDIR /work

ENTRYPOINT ["sam"]

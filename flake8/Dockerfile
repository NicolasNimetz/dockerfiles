FROM python:3.9-alpine

ENV version=4.0.1

## install dependencies in a virtual package before to remove it
RUN apk add --no-cache --virtual .build-deps \
  build-base \
  && pip install --no-cache-dir flake8==$version \
  && apk del .build-deps \
  && addgroup -S flake8 && adduser -S -D flake8 \
  && mkdir /src

# set working directory
WORKDIR /src

## switch to non-root user
USER flake8

CMD ["flake8"]
LABEL name=flake8 version=$version \
    maintainer="Nicolas Nimetz <nicolas.nimetz@icloud.com>"

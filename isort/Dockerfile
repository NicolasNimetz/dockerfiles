FROM python:3.9-alpine

ENV version=5.8.0

## install dependencies in a virtual package before to remove it
RUN apk add --no-cache --virtual .build-deps \
  build-base \
  && pip install --no-cache-dir isort==$version \
  && apk del .build-deps \
  && addgroup -S isort && adduser -S -D isort \
  && mkdir /src

# set working directory
WORKDIR /src

## switch to non-root user
USER isort

CMD ["isort"]
LABEL name=isort version=$version \
    maintainer="Nicolas Nimetz <nicolas.nimetz@icloud.com>"

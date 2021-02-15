FROM python:3.9-alpine

ENV version=20.8b1

## install dependencies in a virtual package before to remove it
RUN apk add --no-cache --virtual .build-deps \
  build-base \
  && pip install --no-cache-dir black==$version \
  && apk del .build-deps \
  && addgroup -S black && adduser -S -D black \
  && mkdir /src

# set working directory
WORKDIR /src

## switch to non-root user
USER black

CMD ["black"]
LABEL name=black version=$version \
    maintainer="Nicolas Nimetz <nicolas.nimetz@icloud.com>"

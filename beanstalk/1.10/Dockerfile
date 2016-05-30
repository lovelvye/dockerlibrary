FROM alpine:3.3

ENV BEANSTALKD_VERSION 1.10

RUN apk add --no-cache --virtual .build-deps \
        tar \
        openssl \
        gcc \
        libc-dev \
        make \
    && wget https://github.com/kr/beanstalkd/archive/v$BEANSTALKD_VERSION.tar.gz \
    && tar xvf v$BEANSTALKD_VERSION.tar.gz \
    && rm v$BEANSTALKD_VERSION.tar.gz \
    && cd beanstalkd-$BEANSTALKD_VERSION \
    && sed -i "s/sys\/fcntl\.h/fcntl\.h/g" sd-daemon.c \
    && make \
    && make install \
    && cd .. \
    && rm -rf beanstalkd-$BEANSTALKD_VERSION \
    && apk del .build-deps

RUN mkdir -p /var/lib/beanstalkd/binlog

WORKDIR /var/lib/beanstalkd/binlog

EXPOSE 11300

CMD ["beanstalkd", "-b", "/var/lib/beanstalkd/binlog", "-F"]

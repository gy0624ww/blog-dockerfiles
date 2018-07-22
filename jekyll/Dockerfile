FROM nginx:1.13.9-alpine

LABEL maintainer="guanyue <gy0624ww@gmail.com>"

ARG TZ='Asia/Shanghai'

ENV TZ ${TZ}

RUN apk upgrade --no-cache --update \
    && apk add --no-cache  bash git \
    && rm -rf /usr/share/nginx/html \
    && git clone https://github.com/gy0624ww/blog-article.git /usr/share/nginx/html \
    && ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
    && echo ${TZ} > /etc/timezone \
    && rm -rf /var/cache/apk/*

COPY entrypoint.sh /root/ #容易报错
# ADD flush /usr/local/bin/flush #容易报错

WORKDIR /usr/share/nginx/html

CMD ["/entrypoint.sh"] #容易报错

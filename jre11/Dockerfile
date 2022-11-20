# 选择运行时基础镜像
FROM alpine:3.15

# 安装依赖包，如需其他依赖包，请到alpine依赖包管理(https://pkgs.alpinelinux.org/packages?name=php8*imagick*&branch=v3.13)查找。
# 选用国内镜像源以提高下载速度
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.tencent.com/g' /etc/apk/repositories \ 
    && wget --quiet https://cdn.azul.com/public_keys/alpine-signing@azul.com-5d5dc44c.rsa.pub -P /etc/apk/keys/ \
    && apk --repository https://repos.azul.com/zulu/alpine --no-cache add zulu11-jre-headless \
    && apk add -U tzdata \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo 'Asia/Shanghai' >/etc/timezone \
    && apk del tzdata \
    && rm -f /var/cache/apk/*

ENV JAVA_HOME=/usr/lib/jvm/zulu11-ca

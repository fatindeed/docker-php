FROM php:7.2-fpm-alpine

# Build-time metadata as defined at http://label-schema.org
ARG BUILD_DATE
ARG VCS_REF
ARG VERSION
LABEL maintainer="James Zhu <168262+fatindeed@users.noreply.github.com>" \
      org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.name="fatinded/php:yaf" \
      org.label-schema.description="PHP with Yaf Data Serialization" \
      org.label-schema.url="https://hub.docker.com/r/fatindeed/php/" \
      org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.vcs-url="https://github.com/fatindeed/docker-php" \
      org.label-schema.vendor="James Zhu" \
      org.label-schema.version=$VERSION \
      org.label-schema.schema-version="1.0"

ARG ALPINE_MIRROR

RUN set -e; \
# Switch to mirror if environment variable exists
    if [ -n "$ALPINE_MIRROR" ]; then \
        sed -i 's!http://dl-cdn.alpinelinux.org!'"$ALPINE_MIRROR"'!g' /etc/apk/repositories; \
    fi; \
    apk add --no-cache --virtual .phpize-deps-configure $PHPIZE_DEPS; \
    pecl install yaf; \
    docker-php-ext-enable yaf; \
    docker-php-source delete; \
    apk del .phpize-deps-configure; \
    runDeps="$( \
        scanelf --needed --nobanner --format '%n#p' --recursive /usr/local/lib/php/extensions \
        | tr ',' '\n' \
        | sort -u \
        | awk 'system("[ -e /usr/local/lib/" $1 " ]") == 0 { next } { print "so:" $1 }' \
    )"; \
    apk add --no-cache --virtual .php-rundeps $runDeps; \
    rm -rf /tmp/pear; \
    rm -rf /usr/local/include; \
    rm -rf /var/cache/apk/*;
FROM php:alpine

# Build-time metadata as defined at http://label-schema.org
ARG BUILD_DATE
ARG VCS_REF
ARG VERSION
LABEL maintainer="James Zhu <168262+fatindeed@users.noreply.github.com>" \
      org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.name="fatinded/php:imagick" \
      org.label-schema.description="PHP with Image Processing (ImageMagick)" \
      org.label-schema.url="https://hub.docker.com/r/fatindeed/php/" \
      org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.vcs-url="https://github.com/fatindeed/docker-php" \
      org.label-schema.vendor="James Zhu" \
      org.label-schema.version=$VERSION \
      org.label-schema.schema-version="1.0"

ARG ALPINE_MIRROR

ENV IMAGEMAGICK_DOWNLOAD_URL="https://www.imagemagick.org/download/ImageMagick.tar.xz"

RUN set -e; \
# Switch to mirror if environment variable exists
    if [ -n "$ALPINE_MIRROR" ]; then \
        sed -i 's!http://dl-cdn.alpinelinux.org!'"$ALPINE_MIRROR"'!g' /etc/apk/repositories; \
    fi; \
# Install build dependency packages
    apk add --no-cache --virtual .phpize-deps-configure $PHPIZE_DEPS freetype-dev libpng-dev libjpeg-turbo-dev fftw-dev; \
# Build and install ImageMagick
    mkdir -p /tmp/imagemagick; \
    curl -fsSL "$IMAGEMAGICK_DOWNLOAD_URL" | tar -Jx -C /tmp/imagemagick --strip-components=1; \
    cd /tmp/imagemagick; \
    ./configure --enable-delegate-build --with-fft; \
    make; \
    make install; \
    ldconfig /usr/local/lib; \
    cd -; \
    rm -rf /tmp/imagemagick; \
# Install PHP extensions
    pecl install imagick; \
    docker-php-ext-enable imagick; \
    docker-php-source delete; \
    apk del .phpize-deps-configure; \
# Install run dependency packages
    runDeps="$( \
        scanelf --needed --nobanner --format '%n#p' --recursive /usr/local/lib \
        | tr ',' '\n' \
        | sort -u \
        | awk 'system("[ -e /usr/local/lib/" $1 " ]") == 0 { next } { print "so:" $1 }' \
    )"; \
    apk add --no-cache --virtual .php-rundeps $runDeps; \
# Cleanup
    rm -rf /tmp/pear; \
    rm -rf /usr/local/include; \
    rm -rf /var/cache/apk/*
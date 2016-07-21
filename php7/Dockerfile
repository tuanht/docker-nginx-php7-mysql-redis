FROM php:7-fpm

RUN docker-php-ext-install pdo_mysql

WORKDIR /tmp

# Install Xdebug
ENV XDEBUG_VERSION 2.4.0
RUN curl -L http://xdebug.org/files/xdebug-$XDEBUG_VERSION.tgz | tar zx \
  && ( \
    cd xdebug-$XDEBUG_VERSION \
    && phpize \
    && ./configure \
    && make \
    && make install \
  ) \
  && rm -rf xdebug-$XDEBUG_VERSION \
  && docker-php-ext-enable xdebug
COPY xdebug.ini /tmp
RUN cat ./xdebug.ini >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
  && rm xdebug.ini

# Install php-redis extension
ENV REDIS_VERSION 3.0.0
RUN curl -L /tmp/redis.tar.gz https://github.com/phpredis/phpredis/archive/$REDIS_VERSION.tar.gz | tar zx \
  && ( \
    cd phpredis-$REDIS_VERSION \
    && phpize \
    && ./configure \
    && make \
    && make install \
  ) \
  && rm -rf phpredis-$REDIS_VERSION \
  && docker-php-ext-enable redis

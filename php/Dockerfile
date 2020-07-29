FROM php:7.0-fpm
RUN apt-get update \
    && apt install libghc-hxt-curl-dev -y \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install mysql \
    && curl -L -o ./redis-4.1.0.tgz http://pecl.php.net/get/redis-4.1.0.tgz \
    && tar zxvf redis-4.1.0.tgz \
    && cd redis-4.1.0 \
    && phpize \
    && ./configure \
    && make && make install \
    && echo "extension=redis.so" > /usr/local/etc/php/conf.d/redis.ini \
    && cd .. \
    && rm -rf redis-4.1.0.tgz redis-4.1.0 \
    && rm -rf /var/cache/apt/* \
    && rm -rf /var/lib/apt/lists/* \
    && echo "alias ll='ls -l'" >> /root/.bashrc 
ADD php.ini /usr/local/etc/php/php.ini

EXPOSE 9000
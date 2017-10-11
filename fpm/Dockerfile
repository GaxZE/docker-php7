FROM ubuntu:latest

RUN apt-get update && apt-get install -y software-properties-common language-pack-en-base \
    && LC_ALL=en_US.UTF-8 add-apt-repository -y ppa:ondrej/php \
    && apt-get update \
    && apt-get install -y php7.0 php7.0-fpm php7.0-mysql mcrypt php7.0-gd curl php7.0-xml php7.0-zip  \
       php7.0-curl php-redis php7.0-mbstring sendmail supervisor nano \
    && mkdir /run/php \
    && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

RUN sed -i -e 's/listen = \/run\/php\/php7.0-fpm.sock/listen = 0.0.0.0:9000/g' /etc/php/7.0/fpm/pool.d/www.conf \
    && sed -i -e 's/;daemonize = yes/daemonize = no/g' /etc/php/7.0/fpm/php-fpm.conf

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
# Composer parallel install plugin
RUN composer global require "hirak/prestissimo"
RUN composer global require "laravel/installer"

RUN export PATH="$PATH:$HOME/.composer/vendor/bin"

WORKDIR /var/app

EXPOSE 9000

CMD ["/usr/bin/supervisord"]
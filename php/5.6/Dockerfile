FROM rainbowmorel/ubuntu:16.04

RUN apt-get clean && apt-get -y update && apt-get install -y locales curl software-properties-common git \
  && locale-gen en_US.UTF-8
RUN LC_ALL=en_US.UTF-8 add-apt-repository ppa:ondrej/php
RUN apt-get update
RUN apt-get install -y --force-yes php5.6-bcmath php5.6-bz2 php5.6-cli php5.6-common php5.6-curl \
                php5.6-cgi php5.6-dev php5.6-fpm php5.6-gd php5.6-gmp php5.6-imap php5.6-intl \
                php5.6-json php5.6-ldap php5.6-mbstring php5.6-mcrypt php5.6-mysql \
                php5.6-odbc php5.6-opcache php5.6-pgsql php5.6-phpdbg php5.6-pspell \
                php5.6-readline php5.6-recode php5.6-soap php5.6-sqlite3 \
                php5.6-tidy php5.6-xml php5.6-xmlrpc php5.6-xsl php5.6-zip \
                php-tideways php-mongodb \
                php5.6-memcached php5.6-redis php-yaml

RUN sed -i "s/;date.timezone =.*/date.timezone = UTC/" /etc/php/5.6/cli/php.ini
RUN sed -i "s/;date.timezone =.*/date.timezone = UTC/" /etc/php/5.6/fpm/php.ini
RUN sed -i "s/display_errors = Off/display_errors = On/" /etc/php/5.6/fpm/php.ini
RUN sed -i "s/upload_max_filesize = .*/upload_max_filesize = 10M/" /etc/php/5.6/fpm/php.ini
RUN sed -i "s/post_max_size = .*/post_max_size = 12M/" /etc/php/5.6/fpm/php.ini
RUN sed -i "s/;cgi.fix_pathinfo=1/cgi.fix_pathinfo=0/" /etc/php/5.6/fpm/php.ini

RUN sed -i -e "s/pid =.*/pid = \/var\/run\/php5.6-fpm.pid/" /etc/php/5.6/fpm/php-fpm.conf
RUN sed -i -e "s/error_log =.*/error_log = \/proc\/self\/fd\/2/" /etc/php/5.6/fpm/php-fpm.conf
RUN sed -i -e "s/;daemonize\s*=\s*yes/daemonize = no/g" /etc/php/5.6/fpm/php-fpm.conf
RUN sed -i "s/listen = .*/listen = 9000/" /etc/php/5.6/fpm/pool.d/www.conf
RUN sed -i "s/;catch_workers_output = .*/catch_workers_output = yes/" /etc/php/5.6/fpm/pool.d/www.conf

RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 9000
CMD ["php-fpm5.6"]

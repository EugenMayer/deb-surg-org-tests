FROM debian:jessie

# install packages.sury.org
RUN apt-get update && apt-get upgrade -y \
  && apt-get install -y curl apt-transport-https lsb-release \ 
  && echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" >> /etc/apt/sources.list.d/packages.sury.org.list \
  && curl https://packages.sury.org/php/apt.gpg -o /tmp/apt.gpg \
  && apt-key add /tmp/apt.gpg && rm /tmp/apt.gpg

# install both base version
RUN apt-get update && apt-get install -y php7.0-common php5.5-common

# install memcached for php7.0 - should work - it will pick up php-memcached
RUN apt-get install -y php7.0-memcached

# install memached for php5.5 - this will fail since it wants to somehow configure against php7.0
RUN apt-get install -y php5.5-memcached

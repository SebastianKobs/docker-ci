FROM ubuntu:18.04

# Timezone
ENV TZ=Europe/Berlin

# Base
RUN export LC_ALL=C.UTF-8 && \
    DEBIAN_FRONTEND=noninteractive && \
    rm /bin/sh && ln -s /bin/bash /bin/sh && \
    ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# APT && COMMON
RUN apt-get update && \
    apt-get install --no-install-recommends -y \
    apt-utils \
    apt-transport-https \
    build-essential \
    bzip2 \
    ca-certificates \
    curl \
    gpg-agent \
    openssh-client \
    rsync \
    software-properties-common \
    ssh \
    sudo \
    unzip \
    wget \
    zip

# PHP
RUN LC_ALL=en_US.UTF-8 add-apt-repository ppa:ondrej/php && \
    apt-get update && \
    apt-get install --no-install-recommends  -y \
    php7.4-bcmath \
    php7.4-bz2 \
    php7.4-cli \
    php7.4-common \
    php7.4-curl \
    php7.4-dev \
    php7.4-gd \
    php7.4-gmp \
    php7.4-imap \
    php7.4-intl \
    php7.4-json \
    php7.4-ldap \
    php7.4-mbstring \
    php7.4-mysql \
    php7.4-pgsql \
    php7.4-soap \
    php7.4-sqlite3 \
    php7.4-xml \
    php7.4-xmlrpc \
    php7.4-xsl \
    php7.4-zip

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    chmod +x /usr/local/bin/composer && \
    composer self-update

# Node.js
RUN curl -sL https://deb.nodesource.com/setup_12.x -o node_setup.sh && \
    bash node_setup.sh && \
    apt-get update && \
    apt-get install -y --no-install-recommends nodejs && \
    npm install npm -g

# SSH
RUN mkdir ~/.ssh && touch ~/.ssh_config
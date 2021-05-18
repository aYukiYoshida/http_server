FROM httpd:2.4

LABEL maintainer="aYukiYoshida <yuki.yoshida@access-company.com>"

USER root
WORKDIR /var/tmp

RUN set -x && \
    : Update package and upgrade installed packages && \
    apt update && apt upgrade -y && \
    apt install sudo

RUN set -x && \
    : Install packages && \
    apt install -y \
    curl \
    gcc \
    libbz2-dev \
    libssl-dev \
    libffi-dev \
    libsqlite3-dev \
    make \
    tk-dev \
    zlib1g-dev \
    apache2-dev \
    python3-dev \
    python3 \
    python3-distutils \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN set -x && \
    : Install mod_wsgi && \
    curl -kLO https://github.com/GrahamDumpleton/mod_wsgi/archive/refs/tags/4.8.0.tar.gz -o mod_wsgi-4.8.0.tar.gz && \
    tar zxf mod_wsgi-4.8.0.tar.gz && cd mod_wsgi-4.8.0 && \
    ./configure \
    --with-apxs=/usr/local/apache2/bin/apxs \
    --with-python=/usr/bin/python3.7 && \
    make && \
    make install

RUN set -x && \
    : Install pip && \
    curl -kL https://bootstrap.pypa.io/get-pip.py | python3

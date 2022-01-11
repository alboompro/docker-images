FROM alboom/ruby-k8s-production:2.7-stretch-with-nodejs

RUN set -eux; \
    apt-get update -qq; \
    apt-get install --no-install-recommends -y \
    build-essential \
    locales \
    curl \
    wget \
    netcat \
    imagemagick \
    libmariadb-dev-compat \
    libmariadb-dev \
    zlib1g-dev \
    tzdata; \
    sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && \
    locale-gen en_US.UTF-8; \
    apt-get clean; \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*


ENV PATH=/usr/local/bin:$PATH
ENV APP_HOME /app

RUN mkdir $APP_HOME

WORKDIR $APP_HOME
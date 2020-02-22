FROM debian:buster

RUN apt-get update -qq && apt-get -yq dist-upgrade && \
    apt-get install -yq --no-install-recommends \
    curl \
    libodbc1 \
    libssl1.1 \
    libsctp1 \
    bash \
    libssl-dev \
    locales \
    zip \
    unzip

RUN echo en_US.UTF-8 UTF-8 >> /etc/locale.gen && locale-gen

RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    truncate -s 0 /var/log/*log

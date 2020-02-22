FROM elixir:1.10.1-slim

RUN apt-get update && apt-get install -y curl

RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -

RUN apt-get update -qq && apt-get -yq dist-upgrade && \
    apt-get install -yq --no-install-recommends \
    build-essential \
    nodejs \
    zip \
    unzip \
    locales \
    git \
    bash

RUN echo en_US.UTF-8 UTF-8 >> /etc/locale.gen && locale-gen

RUN curl -o- -L https://yarnpkg.com/install.sh | bash

RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    truncate -s 0 /var/log/*log

RUN mix local.hex --force && mix local.rebar --force

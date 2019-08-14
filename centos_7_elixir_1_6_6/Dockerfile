FROM centos:centos7

RUN yum update -y && yum clean all
RUN yum install -y wget gcc gcc-c++ glibc-devel make ncurses-devel openssl-devel autoconf java-1.8.0-openjdk-devel git zip && yum clean all
RUN (curl -sL https://rpm.nodesource.com/setup_10.x | bash -) && yum install -y nodejs && npm install -g yarn && yum clean all
RUN wget http://erlang.org/download/otp_src_21.3.tar.gz && tar zxvf otp_src_21.3.tar.gz && pushd otp_src_21.3 && ./otp_build autoconf && ./configure && make -j2 && make install && popd && rm -rf otp_src_21.3.tar.gz && rm -rf otp_src_21.3

ENV ELIXIR_VERSION=1.6.6 \
      LANG=en_US.UTF-8 \
      LANGUAGE=en_US:en \
      LC_ALL=en_US.UTF-8 
WORKDIR /home
RUN git clone https://github.com/elixir-lang/elixir.git && pushd elixir && git checkout refs/tags/v${ELIXIR_VERSION} && make clean install && popd && rm -Rf elixir && mix local.hex --force && mix local.rebar --force

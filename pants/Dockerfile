FROM ubuntu:16.04

RUN apt-get update && apt-get install -y --no-install-recommends \
        python-dev \
        libmysqlclient-dev \
        openjdk-9-jdk-headless \
        python-pip \
        python3 \
        python3-pip \
        python3-dev \
        sudo \
        curl \
        git \
        ruby ruby-dev rubygems build-essential && \
    rm -rf /var/cache/apt/archives

RUN gem install --no-ri --no-rdoc fpm

RUN curl -L "https://github.com/docker/compose/releases/download/1.11.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && chmod +x /usr/local/bin/docker-compose

RUN pip install --upgrade pip setuptools wheel
RUN pip3 install --upgrade setuptools wheel

RUN git clone https://github.com/thesamet/pants /pants-dev

# Get it to bootstrap
WORKDIR /pants-dev
RUN ./pants goals

RUN apt-get install -y --no-install-recommends file
RUN pip install flake8 pep8 awscli

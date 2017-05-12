FROM ubuntu:14.04
RUN apt-get update && apt-get install -y --no-install-recommends software-properties-common

RUN add-apt-repository ppa:fkrull/deadsnakes && \
    add-apt-repository ppa:openjdk-r/ppa

RUN apt-get update && apt-get install -y --no-install-recommends \
        build-essential \
        curl \
        file \
        git \
        libffi-dev \
        libmysqlclient-dev \
        openjdk-8-jdk-headless \
        python3.5 \
        python3.5-dev \
        python3.5-venv \
        python-dev \
        python-pip \
        ruby ruby-dev \
        sudo && \
    rm -rf /var/cache/apt/archives

RUN gem install --no-ri --no-rdoc fpm

RUN curl -L "https://github.com/docker/compose/releases/download/1.11.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && chmod +x /usr/local/bin/docker-compose

RUN python3.5 -m ensurepip

RUN pip install --upgrade setuptools pip && \
    pip3 install --upgrade setuptools pip

RUN pip install --upgrade pip wheel flake8 pep8 awscli
RUN pip3 install --upgrade pip wheel

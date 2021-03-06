FROM ubuntu:18.04
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update
RUN apt-get install -y --no-install-recommends \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common

# RUN add-apt-repository ppa:ubuntu-toolchain-r/test

# make / cmake / git / gcc
RUN apt-get install -y aptitude
RUN apt update && aptitude install -y \
    automake \
    autoconf \
    autotools-dev \
    build-essential \
    cmake \
    debhelper \
    dh-python \
    git \
    gcc-7=7.3.0-16ubuntu3 \
    libboost-regex-dev \
    libgmp-dev \
    libgmp3-dev
    
# RUN update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 60 \
#                         --slave /usr/bin/g++ g++ /usr/bin/g++-7 
# RUN update-alternatives --config gcc
#

# python
RUN apt update && aptitude install -y \
    python-pytest \
    python \
    python3.6 \
    python-pip \
    python-yaml  \
    pypy=5.10.0+dfsg-3build2 \
    tidy

# java
RUN curl -L -o /tmp/java.tar.gz https://download.java.net/java/GA/jdk10/10.0.2/19aef61b38124481863b1413dce1855f/13/openjdk-10.0.2_linux-x64_bin.tar.gz && cd /usr/local && tar zxf /tmp/java.tar.gz && cd /usr/local/bin && ln -s ../jdk*/bin/* .

# kotlin
RUN apt install -y zip
ENV KOTLIN_VERSION 1.3.0
# newer installs
# RUN curl -L -o /tmp/kotlinc.zip https://github.com/JetBrains/kotlin/releases/download/v${KOTLIN_VERSION}/kotlin-compiler-${KOTLIN_VERSION}-linux-x64.zip && cd /usr/local && unzip /tmp/kotlinc.zip && cd /usr/local/bin && ln -s ../kotlinc/bin/* .

RUN curl -L -o /tmp/kotlinc.zip https://github.com/JetBrains/kotlin/releases/download/v${KOTLIN_VERSION}/kotlin-compiler-${KOTLIN_VERSION}.zip && cd /usr/local && unzip /tmp/kotlinc.zip && cd /usr/local/bin && ln -s ../kotlinc/bin/* .

# tex
RUN apt update && aptitude install -y \
    ghostscript \
    python-plastex \
    texlive-generic-recommended \
    texlive-fonts-recommended \
    texlive-lang-cyrillic \
    texlive-latex-extra \
    texlive-latex-recommended
    
# problemtools
RUN mkdir -p /usr/local && cd /usr/local && git clone --recursive https://github.com/kattis/problemtools
RUN cd /usr/local/problemtools && make builddeb
RUN dpkg -i /usr/local/kattis-problemtools_*.deb

WORKDIR /usr/src/myapp
VOLUME /usr/src/myapp

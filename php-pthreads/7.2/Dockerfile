FROM php:7.2-zts
MAINTAINER razonyang@gmail.com

# Install git
RUN apt-get update && \
    apt-get install -y git

ARG PTHREADS_VERSION=master
ENV PTHREADS_REPO https://github.com/krakjoe/pthreads.git
ENV PTHREADS_BUILD_DIR /tmp/pthreads

# Clone repo
RUN git clone $PTHREADS_REPO $PTHREADS_BUILD_DIR
# Build
RUN cd $PTHREADS_BUILD_DIR && \
    git checkout $PTHREADS_VERSION && \
    phpize && \
    ./configure && \
    make && \
    make install
# Add extension file
COPY pthreads.ini $PHP_INI_DIR/conf.d
# Example
COPY downloader /usr/local/bin/pthread-downloader
RUN chmod +x /usr/local/bin/pthread-downloader

CMD ["pthread-downloader"]

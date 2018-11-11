FROM debian:stretch-slim

WORKDIR /

RUN apt-get update && apt-get install -y --no-install-recommends \
		g++ \
		gcc \
		libc6-dev \
		make \
		pkg-config \
    wget \
    unzip
RUN wget http://iobin.suspended-chord.info/linux/iobin-linux-x64-deb-current.zip
RUN unzip iobin-linux-x64-deb-current.zip
RUN dpkg -i IoLanguage-*.deb
RUN rm iobin-linux-x64-deb-current.zip
RUN rm IoLanguage-*.deb

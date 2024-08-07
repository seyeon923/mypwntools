FROM ubuntu:18.04

ENV LC_ALL=C.UTF-8

RUN apt update && apt install -y git wget vim sudo ruby

# Install pwndbg
WORKDIR /usr/local/lib
RUN git clone https://github.com/pwndbg/pwndbg.git
WORKDIR /usr/local/lib/pwndbg
RUN git checkout ubuntu18.04-final
RUN ./setup.sh

# Install one_gadget
RUN gem install one_gadget

# Install Python 
RUN DEBIAN_FRONTEND=noninteractive apt install -y build-essential checkinstall gdb lcov pkg-config \
    libbz2-dev libffi-dev libgdbm-dev liblzma-dev \
    libncurses5-dev libreadline6-dev libsqlite3-dev libssl-dev \
    lzma lzma-dev tk-dev uuid-dev zlib1g-dev libmpdec-dev 

WORKDIR /root
RUN wget https://www.python.org/ftp/python/3.8.19/Python-3.8.19.tgz
RUN tar xf Python-3.8.19.tgz
RUN rm Python-3.8.19.tgz
WORKDIR /root/Python-3.8.19
RUN ./configure --enable-optimizations --with-lto
RUN make install -j16
WORKDIR /root
RUN rm -r Python-3.8.19

# Install pwntools
RUN python3 -m pip install -U pip
RUN python3 -m pip install pwntools

WORKDIR /root

CMD [ "bash" ]
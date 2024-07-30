FROM ubuntu:18.04

RUN apt update && apt install -y git wget vim sudo python3 python3-pip ruby

# Install pwndbg
WORKDIR /usr/local/lib
RUN git clone https://github.com/pwndbg/pwndbg.git
WORKDIR /usr/local/lib/pwndbg
RUN git checkout ubuntu18.04-final
RUN ./setup.sh

# Install one_gadget
RUN gem install one_gadget

# Install pwntools
RUN python3 -m pip install -U pip
RUN python3 -m pip install pwntools

WORKDIR /root

CMD [ "bash" ]
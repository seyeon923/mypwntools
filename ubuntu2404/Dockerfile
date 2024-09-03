FROM ubuntu:24.04

ENV LC_ALL=C.UTF-8

RUN apt update && apt install -y git wget vim sudo

# Install pwndbg
WORKDIR /usr/local/lib
RUN git clone https://github.com/pwndbg/pwndbg.git
WORKDIR /usr/local/lib/pwndbg
RUN git checkout 2024.02.14
RUN DEBIAN_FRONTEND=noninteractive TZ=Etc/UTC apt-get -y install tzdata
RUN ./setup.sh

# Install ruby
RUN apt -y install ruby ruby-dev

# Install one_gadget
RUN gem install one_gadget

# Install Python 
RUN apt install -y python3 python3-pip

# Install pwntools
RUN apt install -y python3-pwntools

WORKDIR /root

# Install seccomp-tools
RUN gem install seccomp-tools

# Install patchelf
RUN apt install -y patchelf

CMD [ "bash" ]
FROM ubuntu:20.04

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
WORKDIR /root

RUN wget https://github.com/postmodern/ruby-install/releases/download/v0.9.3/ruby-install-0.9.3.tar.gz
RUN tar xzf ruby-install-0.9.3.tar.gz
RUN rm ruby-install-0.9.3.tar.gz
WORKDIR /root/ruby-install-0.9.3/
RUN make install
WORKDIR /root
RUN rm -rf ruby-install-0.9.3

RUN ruby-install --update
RUN ruby-install --system ruby 3.3.4

# Install one_gadget
RUN gem install one_gadget

# Install Python 
RUN apt install -y python3 python3-pip

# Install pwntools
RUN python3 -m pip install -U pip
RUN python3 -m pip install pwntools

WORKDIR /root

# Install seccomp-tools
RUN gem install seccomp-tools

# Install patchelf
RUN apt install -y patchelf

# Install ghidra
RUN apt install -y openjdk-21-jdk
WORKDIR /root
RUN wget https://github.com/NationalSecurityAgency/ghidra/releases/download/Ghidra_11.1.2_build/ghidra_11.1.2_PUBLIC_20240709.zip
RUN apt install -y unzip
RUN unzip ghidra_11.1.2_PUBLIC_20240709.zip -d /usr/local/lib
RUN rm ghidra_11.1.2_PUBLIC_20240709.zip
RUN echo 'export PATH=${PATH}:/usr/local/lib/ghidra_11.1.2_PUBLIC' > ~/.bashrc
WORKDIR /root

CMD [ "bash" ]
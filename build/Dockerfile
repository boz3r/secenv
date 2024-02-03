FROM ubuntu:22.04
ENV DEBIAN_FRONTEND=noninteractive
ENV LC_ALL=C.UTF-8

RUN useradd -m lab

WORKDIR /home/lab
RUN apt update --fix-missing && apt dist-upgrade -y
RUN mkdir tools file
RUN apt install -y wget curl vim netcat binwalk file git exiftool steghide rubygems gcc g++ python2 python3 python3-pip  \ 
    john hashcat yara gzip unzip xxd ffmpeg jq apktool ncurses-hexedit auditd

RUN wget https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt
RUN gem install zsteg

WORKDIR /home/lab/tools
RUN  git clone https://github.com/kevthehermit/DuckToolkit.git
WORKDIR /home/lab/tools/DuckToolkit
RUN python3 setup.py install
WORKDIR /home/lab/tools/oledump
RUN wget https://didierstevens.com/files/software/oledump_V0_0_75.zip
RUN unzip oledump_V0_0_75.zip
RUN rm -rf oledump_V0_0_75.zip

WORKDIR /home/lab/tools
RUN git clone https://github.com/Pulho/sigBits.git
RUN git clone https://github.com/TeamRocketIst/ctf-usb-keyboard-parser.git
RUN git clone https://github.com/ragibson/Steganography
RUN git clone https://github.com/sherlock-project/sherlock.git
WORKDIR /home/lab/tools/sherlock
RUN python3 -m pip install -r requirements.txt
WORKDIR /home/lab/tools/Steganography
RUN python3 setup.py install

USER lab

CMD ["/bin/bash"]
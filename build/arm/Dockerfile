FROM ubuntu:22.04
ENV DEBIAN_FRONTEND=noninteractive
ENV LC_ALL=C.UTF-8

WORKDIR /root
RUN apt update \ 
    && apt dist-upgrade -y
RUN mkdir tools file

RUN apt install -y wget curl vim netcat binwalk file git exiftool steghide rubygems gcc python2 python3 python3-pip  \ 
    john hashcat sqlmap gzip unzip xxd foremost apktool ncurses-hexedit && pip3 install Pillow

RUN wget https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt
RUN gem install zsteg

WORKDIR /root/tools
RUN  git clone https://github.com/kevthehermit/DuckToolkit.git
WORKDIR /root/tools/DuckToolkit
RUN python3 setup.py install
WORKDIR /root/tools/oledump
RUN wget https://didierstevens.com/files/software/oledump_V0_0_75.zip
RUN unzip oledump_V0_0_75.zip
RUN rm -rf oledump_V0_0_75.zip

WORKDIR /root/tools
RUN git clone https://github.com/Pulho/sigBits.git
RUN git clone https://github.com/TeamRocketIst/ctf-usb-keyboard-parser.git
RUN git clone https://github.com/ragibson/Steganography
RUN git clone https://github.com/sherlock-project/sherlock.git
WORKDIR /root/tools/sherlock
RUN python3 -m pip install -r requirements.txt
WORKDIR /root/tools/Steganography
RUN python3 setup.py install

WORKDIR /root

CMD ["/bin/bash"]

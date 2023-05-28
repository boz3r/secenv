FROM ubuntu:22.04
ENV DEBIAN_FRONTEND=noninteractive
ENV LC_ALL=C.UTF-8

WORKDIR /root
RUN apt-get update \ 
    && apt-get dist-upgrade -y
RUN mkdir tool chal

RUN apt-get install -y wget curl netcat binwalk file gdb git exiftool steghide ffmpeg ltrace rubygems gcc python2 python3 python3-pip john hashcat sqlmap gzip \
    && pip3 install Pillow

RUN wget https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt
RUN gem install zsteg

WORKDIR /root/tool
RUN git clone https://github.com/pwndbg/pwndbg.git
WORKDIR /root/tool/pwndbg
RUN ./setup.sh

WORKDIR /root/tool
RUN git clone https://github.com/skyf0l/RsaSolver.git
WORKDIR /root/tool/RsaSolver
RUN pip3 install --user -r requirements.txt

WORKDIR /root/tool
RUN  git clone https://github.com/kevthehermit/DuckToolkit.git
WORKDIR /root/tool/DuckToolkit
RUN python3 setup.py install

WORKDIR /root/tool
RUN git clone https://github.com/Pulho/sigBits.git
RUN git clone https://github.com/TeamRocketIst/ctf-usb-keyboard-parser.git

WORKDIR /root

CMD ["/bin/bash"]
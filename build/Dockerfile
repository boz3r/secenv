FROM ubuntu:22.04
ENV DEBIAN_FRONTEND=noninteractive
ENV LC_ALL=C.UTF-8

WORKDIR /root
RUN apt update \ 
    && apt dist-upgrade -y
RUN mkdir tool file

RUN apt install -y wget curl vim netcat binwalk file gdb git exiftool steghide ffmpeg ltrace rubygems gcc python2 python3 python3-pip  \ 
    john hashcat sqlmap gzip lldb xxd foremost apktool ncurses-hexedit && pip3 install Pillow

RUN wget https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt
RUN gem install zsteg

WORKDIR /root/tool
RUN git clone https://github.com/pwndbg/pwndbg.git
WORKDIR /root/tool/pwndbg
RUN ./setup.sh

WORKDIR /root/tool
RUN  git clone https://github.com/kevthehermit/DuckToolkit.git
WORKDIR /root/tool/DuckToolkit
RUN python3 setup.py install

WORKDIR /root/tool
RUN git clone https://github.com/Pulho/sigBits.git
RUN git clone https://github.com/TeamRocketIst/ctf-usb-keyboard-parser.git
RUN git clone https://github.com/ragibson/Steganography
WORKDIR /root/tool/Steganography
RUN python3 setup.py install

WORKDIR /root/tool
RUN curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall && \
    chmod 755 msfinstall && ./msfinstall

WORKDIR /root
CMD ["/bin/bash"]

FROM python:3
LABEL maintainer "Greybeard <gbear@protonmail.ch>"

RUN apt-get update
RUN apt-get install -y libenchant1c2a

RUN useradd -u 1010 -m -d /home/sopel sopel
WORKDIR /home/sopel

RUN pip install git+https://github.com/sopel-irc/sopel.git
RUN pip install Beautifulsoup4 urllib3 sopel-modules.wolfram

VOLUME /home/sopel/.sopel

USER sopel
CMD sopel

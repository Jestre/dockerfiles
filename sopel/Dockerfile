FROM python:3
LABEL maintainer "Greybeard <gbear@protonmail.ch>"

RUN apt-get update && apt-get install -y libenchant1c2a

RUN useradd -u 1010 -m -d /home/sopel sopel

WORKDIR /home/sopel

RUN pip install \
  git+https://github.com/sopel-irc/sopel.git \
  Beautifulsoup4 \
  sopel-modules.wolfram \
  urllib3

VOLUME /home/sopel/.sopel

USER sopel
CMD sopel

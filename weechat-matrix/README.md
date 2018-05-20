weechat-matrix
===================

Forked from: [jkaberg](https://github.com/jkaberg/dockerfiles)

This is an automatically built Alpine Docker image for WeeChat which includes Lua and Lua-cjson so that it will support [torhve's weechat-matrix script](https://github.com/torhve/weechat-matrix-protocol-script). It will (not yet) rebuild everytime there is a new release on [Github](https://github.com/weechat/weechat/releases), but will when the [base image](https://hub.docker.com/_/alpine/) gets updated.


To run it simply use ```docker run```:

``` docker run -it --name weechat -e UID=1000 -e GID=1000 -v /path/to/weechat/config:/weechat greybeard/weechat```

or docker-compose:
```
  weechat:
    image: greybeard/weechat
    restart: always
    stdin_open: true
    tty: true
    volumes:
      - /path/to/weechat/config:/weechat
    environment:
      - 'UID=1000'
      - 'GID=1000'
    networks:
      - some_network
```

Once up and running, use ```ctrl-p```, ```ctrl-q``` to detach from the session and ```docker attach weechat``` to reattach.
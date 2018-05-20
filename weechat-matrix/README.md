weechat-matrix
===================

Forked from: [jkaberg](https://github.com/jkaberg/dockerfiles)

This is an automatically built Alpine Docker image for WeeChat which includes Lua and Lua-cjson so that it will support [torhve's weechat-matrix script](https://github.com/torhve/weechat-matrix-protocol-script). It will (not yet) rebuild everytime there is a new release on [Github](https://github.com/weechat/weechat/releases), but will when the [base image](https://hub.docker.com/_/alpine/) gets updated.


To run it simply use ```docker run```:

``` docker run -it --name matrix -e UID=1000 -e GID=1000 --mount source=weechat-data,target=/weechat  greybeard/weechat-matrix```

or docker-compose:
```
  weechat:
    image: greybeard/weechat-matrix
    restart: always
    stdin_open: true
    tty: true
    volumes:
      - weechat-data:/weechat
    environment:
      - 'UID=1000'
      - 'GID=1000'
    networks:
      - some_network
```

Once up and running, use ```ctrl-p```, ```ctrl-q``` to detach from the session and ```docker attach weechat``` to reattach.

## Matrix Quickstart

If you used a Docker named volume for your data storage as above, then this should have pre-populated the Lua script directory with the `matrix.lua` script.  To configure the basic settings to get connected:

```
  /secure passphrase <a passphrase to secure passwords>
  /secure set matrix <your matrix account password>
  /set plugins.var.lua.matrix.user <your matrix username>
  /set plugins.var.lua.matrix.password \"${sec.data.matrix}\"
```

Other useful commands:

```
  /set weechat.look.prefix_align_max 20
  /set weechat.bar.nicklist.size 20
  /set weechat.bar.status.items [buffer_count],[buffer_plugin],buffer_number+:+buffer_name+{buffer_nicklist_count}+buffer_filter,[hotlist],completion,scroll,matrix_typing_notice
```
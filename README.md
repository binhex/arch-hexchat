**Application**

[HexChat](https://hexchat.github.io/)

**Description**

HexChat is an IRC client based on XChat, but unlike XChat it’s completely free for both Windows and Unix-like systems. Since XChat is open source, it’s perfectly legal. For more info. HexChat was originally called XChat-WDK which in turn was a successor of freakschat.

**Build notes**

Latest stable HexChat release from Arch Linux.

**Usage**
```
docker run -d \
    -p 5900:5900 \
    -p 6080:6080 \
    --name=<container name> \
    --privileged=true \
    -v <path for config files>:/config \
    -v /etc/localtime:/etc/localtime:ro \
    -e WEBPAGE_TITLE=<name shown in browser tab> \
    -e VNC_PASSWORD=<password for web ui> \
    -e UMASK=<umask for created files> \
    -e PUID=<uid for user> \
    -e PGID=<gid for user> \
    binhex/arch-hexchat
```

Please replace all user variables in the above command defined by <> with the correct values.

**Example**
```
docker run -d \
    -p 5900:5900 \
    -p 6080:6080 \
    --name=hexchat \
    --privileged=true \
    -v /apps/docker/hexchat:/config \
    -v /etc/localtime:/etc/localtime:ro \
    -e WEBPAGE_TITLE=Tower \
    -e VNC_PASSWORD=mypassword \
    -e UMASK=000 \
    -e PUID=0 \
    -e PGID=0 \
    binhex/arch-hexchat
```

If you do specify a password for the web ui via the env var 'VNC_PASSWORD' then it MUST be 6 characters or longer, otherwise it will be ignored.

**Access via web interface (noVNC)**

`http://<host ip>:<host port>/vnc.html?resize=remote&host=<host ip>&port=<host port>&&autoconnect=1`

e.g.:-

`http://192.168.1.10:6080/vnc.html?resize=remote&host=192.168.1.10&port=6080&&autoconnect=1`

**Access via VNC client**

`<host ip>::<host port>`

e.g.:-

`192.168.1.10::5900`

**Notes**

User ID (PUID) and Group ID (PGID) can be found by issuing the following command for the user you want to run the container as:-

```
id <username>
```
___
If you appreciate my work, then please consider buying me a beer  :D

[![PayPal donation](https://www.paypal.com/en_US/i/btn/btn_donate_SM.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=MM5E27UX6AUU4)

[Support forum](https://forums.unraid.net/topic/81397-support-binhex-hexchat/)
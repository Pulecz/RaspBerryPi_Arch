# Basic

1. connect to the internet

2. upgrade

 ```bash
# pacman -Syu
```

3. install basic stuff

 ```bash
# pacman -S htop sudo tmux vim
```

4. fix locale

 ```bash
# vim /etc/locale.gen
# locale-gen
```
5. set zone

```bash
# sudo ln -s /usr/share/zoneinfo/Europe/Prague /etc/localtime
```

6. make some scripts for wifi connection

7. check sshd config

# Camera

Read arch wiki for config

need boot config

and PERHAPS the blacklist

```bash
# ln -s /opt/vc/bin/raspi /usr/bin/raspistill
# ln -s /opt/vc/bin/raspivid /usr/bin/raspivid
```

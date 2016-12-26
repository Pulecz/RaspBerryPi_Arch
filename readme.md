# Basic

1. after flashing the SD card via this procedure https://archlinuxarm.org/platforms/armv8/broadcom/raspberry-pi-3

  * connect HDMI cable to some monitor, usb keyboard and power, boot, login as root, root and enable sshd
```bash
# systemctl enable sshd
```

  * if you connected ethernet cable or to connected to wifi now (google arch wiki wifi for that), note which LAN IP you got and continue to step 4.

3. if you didn't connect to internet yet, turn off the pi gracefully (# shutdown now) and connect somewhere just with power and ethernet cable

3. check your router with DHCP server what IP it gave to Pi3, do ssh alarm@${Pi3'sIP}, default password for alarm is alarm

4. create own users and change root password and alarms too, if you don't wish to delete it

  1. as alarm user, switch to root, default password is root
  ```bash
  # su root
  ```

  2.  update (will take some time depending on your sdcard, same for all the installations)

  ```bash
  # pacman -Syu
  ```

  3.  install basic stuff

  ```bash
  # pacman -S htop sudo tmux vim
  ```

  4.  change root's password via

 ```bash
 # passwd
 ```

  and alarm's password via (or delete it after you created your own user)
```bash
# passwd alarm
```

  5.  if you wish to use alarm user, skip this step
    create your own user and set password to it via

  ```bash
  # useradd -m -g wheel user
  # passwd user
  ```

  -m create home folder and -g wheel adds to wheel group usable for sudoers

  then if you wish to delete the alarm user, first log out and login as your new user via ssh, then remove alarm
```bash
@ ssh user@${Pi3'sIP}
# su root
# userdel -r alarm
```

5. edit sudoers to allow users in wheel group to run elevated commands(uncommented line 82) or just specify your user as the one (google arch sudo)

```bash
# EDITOR=vim visudo
```

6. edit locale to your specified languages and run locale-gen (may take some time depending on your sd card)

 ```bash
# vim /etc/locale.gen
# locale-gen
```
7. if you don't like default UTC timezone, set your time zone e.g. CET,

```bash
# rm /etc/localtime
# ln -s /usr/share/zoneinfo/CET /etc/localtime
```
8. edit sshd config if needed

# Camera

Read arch wiki for config

need boot config

and PERHAPS the blacklist

```bash
# ln -s /opt/vc/bin/raspi /usr/bin/raspistill
# ln -s /opt/vc/bin/raspivid /usr/bin/raspivid
`````

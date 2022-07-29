## cleartrace

shell

```
# clear history, not recommended
history -c

# clear current login history
history -r

# do not record history
HISTSIZE=0

unset HISTORY HISTFILE HISTSAVE HISTZONE HISTORY HISTLOG; export HISTFILE=/dev/null; export HISTSIZE=0; export HISTFILESIZE=0

# system log
/var/log/btmp
/var/log/lastlog
/var/log/wtmp
/var/log/utmp
/var/log/secure
/var/log/message

# modify btmp/wtmp/utmp
# ref: https://www.thegeekdiary.com/what-is-the-purpose-of-utmp-wtmp-and-btmp-files-in-linux/
utmpdump /var/log/btmp >/var/log/btmp.file
vi /var/log/btmp.file
utmpdump  -r < /var/log/btmp.file > /var/log/btmp

# modify time
touch -r source target
# can not cheat stat command
stat <file>
stat -x <file> # on OSX

# modify system time
date -s "20220712 18:30:50"
# modify file time, eg: touch -r xxx
hwclock --hctosys

# server app log
nginx
apache
cron

# delete matched ip
sed -i '/192.168.108.33/'d /var/log/messages
# replace login ip addresses
sed -i 's/192.168.166.85/192.168.1.1/g' /var/log/secure
```

vim

```
:set history=0

# clear vim history, not recommended
rm -f ~/.viminfo
```

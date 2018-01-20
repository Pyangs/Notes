- show current language
    $ echo $LANG

- set language
    $ LANG = en_US

- calendar
    $ cal
    $ cal 2009
    $ cal 1 2009

- Caculater
    $ bc

- get help of a command,(manual)
    # man a_command
    $ man cal

- show files about this command
    # man -f a_command
    $ man -f man

- show users on-line
    $ who

- write data of memory to Hard disk
    $ sync

- shutdown 
    # sudo 
    $ shutdown -h now
    $ shutdown -h 20:12
    # send massege to users and reboot
    $ shutdown -r +10 'The system will reboot in 10 mins'
    # send massege to users now
    $ shutdown -k now 'hello'

- reboot 
    # sudo
    $ reboot
    $ halt
    $ poweroff

- run lever, 7 levels in Linux
    # shutdown: level 0
    # command mode    3
    # GUI :     level 5
    # reboot :  level 6

#### ls
- show all files 
    $ ls -a

- show files and details
    $ ls -l

- show all files and details of them in current floder
    $ ls -al 

-rw-r--r--  1 pyangs pyangs        5 12月  2 03:31 upstart-udev-bridge.1178.pid
drwxr-xr-x  2 pyangs pyangs     4096 12月  9 16:22 桌面
type and rights--files connect to it----belong to-date-----name
'd' for folder
'-' for file

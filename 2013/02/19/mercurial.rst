Mercurial
=========

.. highlight:: console

I am planning to use the distributed revision control software Mercurial_ for my Org-mode_ files. Fortunately this is quite easy to set up. Especially when you have Ubuntu/Debian on a server and a client. When the client also has ssh access to the server, just do this:

.. _Mercurial: http://mercurial.selenic.com/
.. _Org-mode: http://orgmode.org/

On the server
----------------------------

Install Mercurial and set up a repository::

    $ sudo apt-get install mercurial
    $ mkdir hg-test
    $ cd hg-test/
    $ hg init

On the client
-------------

Install Mercurial and clone the repository::

    $ sudo apt-get install mercurial
    $ hg clone ssh://sshuser@sshserver/hg-test/

Set up your identity in ``~/.hgrc``:

.. code-block:: ini

    [ui]
    username = Your Name <your.name@example.net>

Make some changes::

    $ cd hg-test/
    $ touch a_file.txt
    $ hg add a_file.txt
    $ hg commit -m "added a file"
    $ hg push

Check, what you have done::

    $ hg log

Read the documentation
----------------------

1. http://mercurial.selenic.com/wiki/Tutorial
2. http://hgbook.red-bean.com/

.. author:: default
.. categories:: none
.. tags:: none
.. comments::

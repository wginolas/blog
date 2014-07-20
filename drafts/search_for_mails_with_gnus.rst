Searching and processing mails with Gnus
========================================

I am using Gnus_ to read mail for some time now, but I was always using other tools, to search for mails and organise them. After reading the docs, I found out, that Gnus is (of course) quite powerful in this tasks.

:: _Gnus: http://www.gnus.org/

Setting everything up
---------------------

Even though we are talking about Emacs here, there is actually nothing to set up! (If you are using the ``imap`` engine.)

Searching in Groups
-------------------

In the ``*Group*`` buffer you can type ``G G`` and search in the group, your cursor is on. With ``C-u G G`` you can also specify in which part of the emails you want to search. Boolean operators (``AND``, ``OR`` and ``NOT``) can also be used in search queries.

Seatch group: G G 

Query Syntax
C-u G G

Mark and search groups

   Also see the `&' command in *note Searching for Articles::, for how
to set process marks based on article body contents.

Do something on marks M-&

.. author:: default
.. categories:: none
.. tags:: gnus, emacs
.. comments::

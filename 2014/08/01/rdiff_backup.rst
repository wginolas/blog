rdiff-backup
============

.. highlight:: bash

rdiff-backup_ is a great tool, to make a local backup of a directory. Even though this will not save your files from a hard disk failure, you will be able, to restore data you lost due to your own mistakes.

.. _rdiff-backup: http://www.nongnu.org/rdiff-backup/

Making a backup of a directory works like this::

  $ rdiff-backup some-dir backup-of-some-dir

When you call this the first time, rdiff-backup will simply copy ``some-dir`` to ``backup-of-some-dir``. When you call this command again, two things will happen:

1. The copy in ``backup-of-some-dir`` will be updated, to reflect the current state of ``some-dir``.
2. A *inverse* increment will be created, which can be used, to restore the last sate of ``some-dir``.

Those inverse increments are usually quite small, so you can easily keep weeks or months of daily backups.

I am using a cron job, to make a daily backup::

  #!/bin/sh

  rdiff-backup --remove-older-than 60D --force /home/wolfgang/backup/rdiff/home
  rdiff-backup --include-globbing-filelist /home/wolfgang/bin/home.include /home/wolfgang/ /home/wolfgang/backup/rdiff/home

As you can see, this will backup my home directory. I am also removing backups, that are older than 60 days. The ``--include-globbing`` parameter will restrict the backup to some directories. ``home.include`` looks like this:

.. code-block:: text

  /home/wolfgang/Dropbox
  /home/wolfgang/org
  /home/wolfgang/bin
  /home/wolfgang/.emacs
  /home/wolfgang/.bbdb
  /home/wolfgang/.aspell*
  /home/wolfgang/.gitconfig
  /home/wolfgang/.zshrc
  /home/wolfgang/SOME_OTHER_FILES_AND_DIRECORIES_I_WANT_TO_SAVEare/df_linux
  - **

Those lines will include files and directories in the backup. The last line will exclude everything else.

To be able to restore your files, when you have physical problem with your disk, you should regularly sync your backup to a USB stick, or a cloud storage.

.. author:: default
.. categories:: none
.. tags:: backup, cron
.. comments::

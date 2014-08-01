Clean up Downloads
==================

As Lifehacker.com_ suggests, you can use the ``/tmp`` folder for files which you only need for a short time. Those files are deleted on the next reboot. I like the idea, that I do not have to clean up my temporary files. Especially files in my ``Downloads`` folder. However, I do not like the idea, that those files are deleted on every reboot, i.e. daily. So I wrote a little Python script to remove downloads that are older than 30 days::

    #!/usr/bin/python

    import os
    import shutil
    import time
    import logging

    CLEAN_FOLDERS = ["~/dummy", "~/Downloads"]
    MAX_AGE = 30 * 24 * 60 * 60 # 30 days in seconds

    def main():
        logging.basicConfig(
            filename=os.path.expanduser('~/logs/dir-cleanup.log'),
            level=logging.INFO,
            format='%(asctime)s %(message)s')
        logging.info("Starting to clean up")
        now  = time.time()
        for c in [os.path.expanduser(p) for p in CLEAN_FOLDERS]:
            for file_name in os.listdir(c):
                full_path = os.path.join(c, file_name)
                file_time = os.path.getmtime(full_path)
                if file_time + MAX_AGE < now:
                    logging.info("Deleting %s", full_path)
                    if os.path.isdir(full_path):
                        shutil.rmtree(full_path, ignore_errors=True)
                    else:
                        os.remove(full_path)

    if __name__ == "__main__":
        main()


.. _Lifehacker.com: http://lifehacker.com/352169/use-a-tmp-folder-in-os-x-to-keep-your-desktop-clean

.. highlight:: bash

As you see, this script also cleans my ``dummy`` folder where keep my temporary stuff, like screen shots I attached to bug reports. To run this script daily, I dropped a file with this content to ``/etc/cron.daily``::

    #!/bin/sh -e

    su -c "/home/wolfgang/bin/dir-cleanup.py" wolfgang


.. author:: default
.. categories:: none
.. tags:: cron, python
.. comments::

Custom Unity launcher
=====================

.. highlight:: ini

If you are using Unity, and want to add custom applications to the starter, you can do the following:

1. Create a file ``~/.local/share/applications/YOUR_APPLICATION.desktop`` like this::

    [Desktop Entry]
    Type=Application
    Name=Emacs
    Comment=Emacs
    Icon=/home/wolfgang/software/emacs-24.3/etc/images/icons/hicolor/48x48/apps/emacs.png
    Exec=/home/wolfgang/software/emacs-24.3/src/emacs
    Terminal=false
    Categories=Development;IDE;

2. Open ``~/.local/share/applications/`` in a file browser and drag ``YOUR_APPLICATION.desktop`` to the Unity launcher on the left side.

.. author:: default
.. categories:: none
.. tags:: unity
.. comments::

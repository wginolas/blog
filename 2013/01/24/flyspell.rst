Flyspell
========

.. highlight:: cl

I like coding in Emacs. However sometimes, I have to write texts in human languages (mails, blog posts, ...). Thankfully there is flymake. flymake highlights misspelled words in your Emacs buffer. Since I write texts in different languages, I defined two commands in my ``~/.emacs``::

    (defun british ()
      (interactive)
      (ispell-change-dictionary "british")
      (flyspell-mode)
      (flyspell-buffer))
    
    (defun german ()
      (interactive)
      (ispell-change-dictionary "de")
      (flyspell-mode)
      (flyspell-buffer))

This way I can start the spell checker with ``M-x british`` or ``M-x german``. To stop flymake I type ``M-x flyspell-mode``.

.. author:: default
.. categories:: none
.. tags:: emacs
.. comments::

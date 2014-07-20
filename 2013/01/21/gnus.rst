Gnus
====

As Emacs user I - of course - really like to do everything in Emacs. Fortunately Rodrigo Wanderley described his mail setup in this article_, and here is how I use Gnus to read my mail.

.. _article: http://linil.wordpress.com/2008/01/18/gnus-gmail/

My ~/.gnus.el
-------------

.. code-block:: cl

    ; Gnus
    (require 'gnus)
    
    ; Use IMAP to fetch mails.
    (setq gnus-select-method '(nnimap "gmail"
                                      (nnimap-address "imap.gmail.com")
                                      (nnimap-server-port 993)
                                      (nnimap-stream ssl)))
    
    ; Make Gnus NOT ignore [Gmail] mailboxes.
    (setq gnus-ignored-newsgroups "^to\\.\\|^[0-9. ]+\\( \\|$\\)\\|^[\"]\"[#'()]")
    
    ; Use SMTP to send mails.
    ; See also: http://linil.wordpress.com/2008/01/18/gnus-gmail/
    (setq user-full-name "Full Name")
    (setq user-mail-address "full.name@googlemail.com")
    (setq smtpmail-starttls-credentials '(("smtp.gmail.com" 587 nil nil))
          smtpmail-smtp-server "smtp.gmail.com"
          smtpmail-default-smtp-server "smtp.gmail.com"
          send-mail-function 'smtpmail-send-it
          message-send-mail-function 'smtpmail-send-it
          smtpmail-smtp-service 587
          smtpmail-auth-credentials "~/.authinfo")
    
    
    ; Look for new mails every 10 minutes, when emacs was idle for 1 minute.
    (gnus-demon-add-handler 'gnus-demon-scan-news 10 1)
    
    ; Hook to sign all messages with gpg. gpg will use the "default" private key, which is
    ; the first key in the secret keyring.
    (add-hook 'message-send-hook 'mml-secure-message-sign-pgpmime)
    
    ; Use BBDB ass address book.
    (require 'bbdb)
    (bbdb-initialize 'gnus 'message)


My ~/.authinfo
--------------

.. code-block:: text

    machine imap.gmail.com login full.name@justsoftwareag.com password <my password> port 993
    machine smtp.gmail.com login full.name@justsoftwareag.com password <my password>


Some useful Keystrokes
----------------------

======= ======
Key     Effect
======= ======
In main view
--------------
l       List all folders with unread mail.
L       List all folders.
g       Look for new mails on the server.
RET     Show unread mails in folder.
C-u RET Show all mails in folder.
m       Write a new mail.
In group view
--------------
q       Back to main view.
SPACE   Read selected mail.
E       Mark mail as expirable. Gnus will delete this mail in a week.
!       Mark mail as important.
M c     Clear all marks on the mail.
B m     Move mail to another folder.
B c     Copy mail to another folder.
======= ======

.. author:: default
.. categories:: none
.. tags:: gnus, emacs, mail
.. comments::

Woof
====

Wie ja bereits festgestellt_ wurde, kann man vor diversen Hürden stehen, wenn man mal eben eine Datei von einem Rechner auf den anderen übertragen will. Selbst dann, wenn beide Rechner nebeneinander stehen, und sich das gleiche Netz teilen.

.. _festgestellt: https://xkcd.com/949/

Mir hat da letztens ein ``apt-get install woof`` geholfen. Woof ist ein einfacher HTTP-Server, der eine einzelne Datei zum Download anbietet. Auch ein Datei-Upload ist möglich.

.. code-block:: console

 Woof (Web Offer One File) is a tool to copy files among hosts. It can serve a
 specified file on HTTP, just for a given number of times, and then exits.
 
 It can be easily used to share files across the computers on a net, enough the
 other ends have just a browser (that means you can share things between
 different operating systems or different devices, even phones).
 
 Features include:
  * it can share stuff "one shot" and exit just after he served that file.
  * it can share things among different operating system or different devices
    (e.g.: a smartphone), and allows one to upload files easily.
  * it can also show a simple html form in order to upload file (useful if the
    client hasn't a way to serve the file).

.. author:: default
.. categories:: none
.. tags:: none
.. comments::

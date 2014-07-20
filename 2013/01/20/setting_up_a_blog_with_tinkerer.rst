Setting up a Blog with Tinkerer
===============================

Installation
------------

.. code-block:: console

    $ virtualenv tinkerer
    $ . tinkerer/bin/activate
    (tinkerer)$ pip install Tinkerer


Set up the Blog
---------------

A Blog can be set up as described in the `Tinkerer Documentation`_:

.. _Tinkerer Documentation: http://www.tinkerer.me/pages/documentation.html

.. code-block:: console

    $ mkdir blog
    $ cd blog/
    $ tinker --setup


First post
----------

.. code-block:: console

    $ tinker --post 'Hello World!'
    New post created as 'blog/2013/01/19/hello_world_.rst'

Btw, I found this_ page quite useful, to learn *reStructuredText*.

.. _this: http://people.ee.ethz.ch/~creller/web/tricks/reST.html


Hello World!
------------

Create your blog with:

.. code-block:: console

    $ tinker --build

... and look at it here: ``blog/html/index.html``.

.. author:: default
.. categories:: none
.. tags:: tinkerer, rst
.. comments::

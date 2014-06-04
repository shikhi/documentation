.. _devenv:

.. sectionauthor:: Bernhard Posselt <dev@bernhard-posselt.com>

=======================
Development Environment
=======================

Please follow the steps on this page to set up your development environment.

Set up web server and database
==============================

First `set up your web server and database <http://doc.owncloud.org/server/7.0/admin_manual/installation.html>`_ (**Section**: Manual Installation - Prerequisites).

Get the source
==============

There are two ways to obtain ownCloud sources: 

* Using the `stable version <http://doc.owncloud.org/server/7.0/admin_manual/installation.html>`_
* Using the development version from `GitHub`_ which will be explained below.

To check out the source from `GitHub`_ you will need to install git (see `Setting up git <https://help.github.com/articles/set-up-git>`_ from the GitHub help)

Gather information about server setup
-------------------------------------

To get started the basic git repositories need to cloned into the web server's directory. Depending on the distribution this will either be

* **/var/www**
* **/var/www/html** 
* **/srv/http** 


Then identify the user and group the web server is running as and the Apache user and group for the **chown** command will either be

* **http**
* **www-data** 
* **apache**

Check out the code
------------------

The following commands are using **/var/www** as the web server's directory and **www-data** as user name and group.

.. note:: Python 3.4 includes pip by default

Install the development tool (**depends on Python 3 and python3-pip**)::

   sudo pip3 install ocdev

.. ocdev fails with python2.7 and python3, unsure what it was supposed to do. (jw)

Make the directory writable::

  sudo chmod o+rw /var/www
  
.. Then install ownCloud from git::
.. 
..   ocdev setup base

  cd /var/www
  git clone git@github.com:owncloud/core.git
  git submodule update --init

Adjust rights::

  sudo mkdir -p /var/www/core/data/
  sudo chown -R www-data:www-data /var/www/core/data/
  sudo chmod o-rw /var/www


Finally restart the web server (this might vary depending on your distribution)::

  sudo systemctl restart httpd.service

or::

  sudo /etc/init.d/apache2 restart

After the clone Open http://localhost/core (or the corresponding URL) in your web browser to set up your instance.

Enabling debug mode
-------------------
.. _debugmode:

.. note:: Do not enable this for production! This can create security problems and is only meant for debugging and development!

To disable JavaScript and CSS caching the option DEBUG has to be added to the end of the :file:`core/config/config.php` file. Several other options exist and can be by placed inside the $CONFIG array.

::

   'loglevel' => '0',
   'logquery' => true,
   'cron_log' => true,
   'apps_paths' => array(
     array('path'=>'/var/www/core/apps',  'url'=>'/apps',  'writable'=>true),
     array('path'=>'/var/www/core/apps1', 'url'=>'/apps1', 'writable'=>true),
   ),
  }
  DEFINE('DEBUG', true);

The additional apps1 shown above allows us to checkout the apps.git repo 
like this::

  cd /var/www/core/
  git clone git@github.com:owncloud/apps.git apps1

More configuration ideas can be seen in :file:`core/config/config.sample.php`

.. _GitHub: https://github.com/owncloud
.. _GitHub Help Page: https://help.github.com/


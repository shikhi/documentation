Troubleshooting
===============

Debugging an Issue
------------------

In a standard ownCloud installation the log level is set to "Normal". However, to troubleshoot any issues you might need to raise the log level to "All" from the Admin page.

Some logging (for example, JavaScript console logging) requires manually editing the
configuration file. For this type of logging, open :file:`config/config.php` in a text editor and add ``define('DEBUG', true);``.  For example::

    <?php
    define('DEBUG',true);
    $CONFIG = array (
        define('DEBUG', true);
    );

For JavaScript issues you must also view the JavaScript console. All major browsers
provide developer tools for viewing the console, and you usually access them by
pressing F12. For Firefox, we recommend installing the `Firebug extension <https://getfirebug.com/>`_.

Service Discovery
-----------------

Some clients (especially iOS) have problems finding the proper synchronization URL, even when explicitly configured to use it.

There are several techniques to remedy this, which are described extensively at the
`Sabre DAV website <http://sabre.io/dav/service-discovery/>`_.

Apple iOS
`````````

.. note:: The following has been tested using iOS (including iOS 7).

If your ownCloud instance is installed in a sub-folder under the web servers document root, and the client has difficulties finding the Cal- or CardDAV end-points:

1. Configure your web server to redirect from a "well-know" URL to the one used by ownCloud. 

  When using the Apache web server, you can redirect using a :file:`.htaccess` file in the document root of your site. For example, say your instance is located in the ``owncloud`` folder, so the URL to it is ``ADDRESS/owncloud``.  To redirect, create or edit the :file:`.htaccess` file and add the following lines::

    Redirect 301 /.well-known/carddav /owncloud/remote.php/carddav
    Redirect 301 /.well-known/caldav /owncloud/remote.php/caldav

  When using a Nginx web server, the setting looks similar to the following::

    url.redirect = (
        "^/.well-known/carddav" => "/owncloud/remote.php/carddav",
        "^/.well-known/caldav" => "/owncloud/remote.php/caldav",
    )

2. Once you have configured the redirect, change the URL in the client settings to use ``ADDRESS`` instead of ``ADDRESS/remote.php/carddav/principals/username``.

  .. note:: You can find added information about configuring the redirect in the `forum <http://forum.owncloud.org/viewtopic.php?f=3&t=71&p=2211#p2197>`_.


BlackBerry OS 10.2
``````````````````

BlackBerry OS up to 10.2.2102 doesn't accept a URL with protocol ``https://`` in front of the server address.
It will always tell you, that it cannot login on your server. So instead of writing

    https://address/remote.php/carddav/principals/username
    
in the server address field, you have to write

    address/remote.php/carddav/principals/username


Updating Contacts or Events
---------------------------

If you receive an error like ``PATCH https://ADDRESS/some_url HTTP/1.0 501 Not Implemented`` it is likely a result of one of the following:

* Problem: An outdated lighttpd web server -- lighttpd in debian wheezy (1.4.31) does not support the PATCH HTTP verb.
  Solution: Upgrade to lighttpd greater than or equal to version 1.4.33.

* Problem: You are using Pound reverse-proxy/load balancer -- Pound does not currently support the HTTP/1.1 verb.
  
  Solution: Install the Pound `patch <http://www.apsis.ch/pound/pound_list/archive/2013/2013-08/1377264673000>`_ to support HTTP/1.1.

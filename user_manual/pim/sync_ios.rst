iOS - Synchronize iPhone/iPad
=============================

This topic describes how to synchronize the your calendars and contacts to your iOS device. 

Synchronizing Your Calendar
---------------------------

To synchronize your calendar:

#. Open the settings application on your iPhone/iPad.
#. Select Mail > Contacts > Calendars.
#. Select ``Add Account``.
#. Select ``Other`` as the account type.
#. Select ``Add CalDAV account``.
#. For server, enter the following:
   ``ADDRESS/remote.php/caldav/principals/username``
#. When prompted, enter your username and password.
#. Select ``Next``.
   If your server does not support SSL, a warning is displayed.
#. Select ``Continue``.
#. If the iOS devices is unable to verify the account information, perform the
   following:

   a. Select OK.
   b. Select advanced settings.
   c. Make sure Use SSL is set to OFF.
   d. Change port to 80.
   e. Go back to account information and hit Save.

Your ownCloud calendar becomes visible in the iOS device Calendar application.


Synchronizing Your Address Book
-------------------------------

#. Open the settings application.
#. Select Mail > Contacts > Calendars.
#. Select ``Add Account``.
#. Select ``Other`` as the account type.
#. Select ``Add CardDAV account``.
#. For server, enter the following:
   ``ADDRESS/remote.php/carddav/principals/username``
#. When prompted, enter your user name and password.
#. Select ``Next``.
   If your server does not support SSL, a warning is displayed.
#. Select ``Continue``.
#. If the iOS device is unable to verify the account information, perform the
   following:

   a. Select OK.
   b. Select advanced settings.
   c. Make sure Use SSL is set to OFF.
   d. Change port to 80.
   e. Go back to account information and hit Save.

Your ownCloud contacts become visible in the address book of your iOS device.

.. note:: If you do not see the changes in your iOS device, please refer to 
   the :doc:`troubleshooting` guide.
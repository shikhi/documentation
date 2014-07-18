Synchronizing Thunderbird Address Book
======================================

This topic describes how to synchronize your ownCloud contacts with the Thunderbird Address Book.

These procedures require that you have both Thunderbird and SoGo Connector installed.  You can use the following links locate and install these applications:

* `Thunderbird <http://www.mozilla.org/en-US/thunderbird/>`_ for your OS unless it comes with your OS distribution (Linux)
* `SoGo Connector <http://www.sogo.nu/english/downloads/frontends.html>`_ (latest release)

With the Thunderbird mail application and SoGo Connector installed, you can synchronize Thunderbird Address Book as follows:

1. Open the Thunderbird Address Book, located in the Thunderbird "Tools" Menu.

2. Migrate to File > New > Remote Addressbook 

   .. note:: The SoGo Connector application added this option to the menu.

3. Specify a name for the address book. This name appears in the Thunderbird addressbook bar.

4. Specify the URL located in your ownCloud Contacts area.  To locate the URL:

   a. Access the ownCloud Contacts app.
   
   b. Locate the gear button and click it to open the Contacts settings.

      .. image:: ../images/contact_thunderbird-Symbol_Gear.jpg

   c. Locate and click the impeller symbol.

      .. image:: ../images/contact_thunderbird-Symbol_Impeller.jpg

      The URL you need for your installation is displayed.

      .. image:: ../images/contact_thunderbird-URL_config.jpg

5. Right-click on your newly created address book and select ``Synchronize`` from the menu.

   The address book populates from ownCloud. 
	  
6. (Optional) Specify that the address book is "read only".  The read only setting disallows modifications of the address book in ownCloud.  This includes changes to the contact information as well as the ability to move the address book to another location.

The remaining configuration for the Thunderbird address book is self-explanatory. However, for added information about using the Thunderbird address book (for example, moving contacts from one address book to another), refer to the application documentation.

.. note:: Use caution when moving (dragging and dropping) contacts between address books.  Moving a contact from an ownCloud address book to a personal address book removes the contact from the ownCloud server (and deletes it from all other synchronized connections) and places the contact in your local address book ONLY.  If you are concerned about losing any contacts, we recommend that you save them to a VCF file (or LDIF file using the Thunderbird address book).

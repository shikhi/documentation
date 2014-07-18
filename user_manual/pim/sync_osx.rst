Synchronizing with Apple OS X Devices
=====================================

To use ownCloud with iCal you will need to use the following URL::

    http://ADDRESS/remote.php/caldav/principals/username/

The setup is similar to the setup for iOS, using the path **ADDRESS/remote.php/caldav/principals/username/** to sync with ownCloud.

# ??Similar? It looks identical. What is it that we need to point out here?  Is there another procedure that covers this?

For OS X 10.7 Lion and 10.8 Mountain Lion synchronization functions as expected.  However, for OS X 10.6 (Snow Leopard) and older releases, you might have to perform the following:

# You mention "addressbook" like it's an application.  I don't see an "addressbook" application on any Apple devices I have access to.  I see "Contacts" as an application.  How does this differ from "addressbook"?  To alleviate this, I have changed "addressbook" to "your address book" to be more generic.  Is this acceptable?  

1. Ensure that your address book application is not running. 
   If necessary, to terminate the address book application, select the windows and press Command + Q to terminate it.  
   
# ??What is meant by "select the windows"?  What windows?  If we're in an Apple product, why are we using "Command + Q"??
   
2. Navigate to ``/Users/YOUR\_USERNAME/Library/Application Support/AddressBook/Sources``. 
   If you already have an address book setup, you might see some folders with names like **BEA92826-FBF3-4E53-B5C6-ED7C2B454430**. 
   
# ??Navigate from where?  In what?  Are we doing this on the iOS device?  What are the folders you're pointing out?  What is their significance??
   
3. Make a list of the folders that reside in the ``Sources`` directory and leave the window open.

4. Open the address book and attempt to add a new CardDav address book. 

   At this point, it does not matter what information you enter. The address book returns the same error message when you click "Create". 
   
# ??This is the first time clicking "Create" is mentioned in these instructions.  I can only guess that you are referring to other instructions, but I don't know where they are or what they are dealing with.  Can you elaborate??
   
5. Ignore the error message and click "Create" again. 
   
   A non-functional address book is added.
   
# ??Seems a bit klugey, doesn't it?  Is this a bug??
   
6. Close the address book using ``Command + Q``.

# ??Same question about using "Command + Q" ... why are we using it?  Can we simply say "Close the address book"??

7. Return to the folder window. 

   A newly created folder appears with another long string as its name.
   
# ??Do you mean go back to the /Users/YOUR\_USERNAME/Library/Application Support/AddressBook/Sources directory??
   
8. Open the newly created folder.

# ??So we want the customer to compare all files that they wrote down at the beginning of this procedure and find the one that wasn't there before??

9. Locate the *Configuration.plist* file and open it in a text editor.

10. Search for a section that looks like the following::

    <key>servername</key> <string>http://:0(null)</string> <key>username</key> <string>Whatever_you_entered_before</string>
	
# ??I really don't have a clue what this means.  "Whatever_you_entered_before" where?  In what procedure is this located??  

11. Modify the section to look like the following::

    <key>servername</key <string>http://YOUR_DOMAIN:80/owncloud/remote.php/carddav/principals/username</string> <key>username</key <string>username</string>
	
	.. note:: It is important that you include the :80 after **YOUR_DOMAIN**.
	
# ??So change the string to something similar to what you provide.  Yes?  Would an example of what it actually looks like be better here??

12. Save the file and open the address book again. 

    .. note:: The address book does not yet function.
	
# ??Well that stinks.  How does the user actually know it isn't working?  What do they see?  WHY doesn't it work?  Perhaps we say something like, "Because of 'blah blah blah', the address book won't function."  Just telling them to do something without explaining why might become frustrating.??

13. Open the preferences for your ownCloud CardDAV-Account and enter your password.

# ??Not sure where that is. A screen capture would help.  So is this found in the Contacts app settings somewhere?  In the Admin settings?  Can you point me to where this is done??

14. If the address book does not function, restart it again. 

    The address book should begin working.  If it still does not function, refer to the :doc:`troubleshooting` guide for assistance.
	
# ??Ouch.  After all that, it might still not work?  What are the odds of it not working?  This sounds like a bug workaround more than instructions for using the product.??

    .. note:: You can find a helpful `HOWTO`_ in the forum for assistance.


.. _HOWTO: http://forum.owncloud.org/viewtopic.php?f=3&t=132

# ??Should that information be folded in here??

# Misc 

## How do I migrate/move settings?
Create a database backup in the settings menu. Then choose restore database to import settings in another app - this will overwrite existing settings so beware. That's its. This will work between lite and pro version as well.

## On Android 11 <sdcard>/Android/data folder can no longer be accessed, why?
Android 11 has new file permission requirements and has restricted access to certain folders, like the data folder. It may be possible to add a specific Storage Access Framework permission on permissions screen to allow access to this folder, but unfortunately this will not work on all devices and may stop working completely in the future if Google wants it to.

Note: Built-in vendor file managers can still access protected folders in some cases.

## Why are my transfer speeds slow?
Transfer speeds can be slow for many reasons and can vary from device to device. FTPS/SFTP speeds can potentially be increased by disabling compression, since this limits how much data can be sent by how fast the CPU can compress the data. The speed of the memory card can also influence transfer speeds of course.
Transfer speeds have been compared to other popular file managers and they are comparable on the devices we test on, but we are aware that users on some device experience lower speeds.

## Why can't FolderSync be moved to the SD card?
Unfortunately this feature will not be enabled, since it can cause scheduled syncs not to work and then a lot of users will probably complain. :-) However, if you have a rooted phone you can use this tool to move any app to SD:
[https://market.android.com/details?id=com.leinardi.setinstalllocation](https://market.android.com/details?id=com.leinardi.setinstalllocation)

Just as long as you know that doing so may cause scheduled syncs not to work correctly.

## How do I use Tasker to run a sync in FolderSync?
First of all the full version is required. The full version works as a Tasker plugin - when you configure a new task in Tasker you are presented with a number of Action categories, one of these being "Plugin". Select this and then select "FolderSync" plugin action. Then press edit and select the folderpair you wish to start syncing with this task is executed by Tasker. Then save the task as you normally would in Tasker. For a more general introduction to tasker go here:
http://tasker.dinglisch.net/faq.html

## HTTPS connection errors
This can happen on newer Android devices, since deprecated encryption ciphers are no longer enabled by default with OkHttp/Android to increase security. This means, if you are connecting to an insecure web server using WebDAV or ownCloud, the connection may fail. You can either upgrade your server or try to enable self-signed certificates for you WebDAV/ownCloud account. See here which protocols/ciphers are supported on which Android versions: [https://developer.android.com/reference/javax/net/ssl/SSLEngine.htm](https://developer.android.com/reference/javax/net/ssl/SSLEngine.htm)

## How do I fix getting stuck on web page when trying to authenticate account?
When using external browser or custom Chrome tab to authenticate Google Drive or other OAuth supported cloud providers some can get stuck on the web page that gets redirected to. The cause of this is the app is not opened as it should when the https://www.tacit.dk/oauth-return url is loaded. To remedy this please ensure you are using Chrome as your default browser and it is the latest version. Also try to clear defaults for Chrome if still not working.

## How can I access internal SD card, external SD card and USB OTG drive?
To be able to access internal and external SD card, USB OTG and Android/data folder the the necessary permissions must be granted to the app. You do this on the permissions screen that can be opened on about page (right-most option in the bottom menu). It will display which permissions are required by the app and the status of these - and most importantly give you an option to grant the permissions, if they are missing. 

Its also important to note, that if you change your SD card, you must regrant permissions for that SD card to FolderSync or the new SD card won't have write access. You must do this everytime you change SD card, no matter if a SD card has been previously granted permissions. If you decided FolderSync should no longer have write access to external SD card, you can revoke its permissions in settings.

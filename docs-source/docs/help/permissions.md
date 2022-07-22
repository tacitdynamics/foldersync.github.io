# Permissions

For FolderSync to function correctly, it must have the required permissions granted. On the welcome wizard on the first run of the app you should se a permissions screen with a overview of these permissions and how to grant them. The permissions screen can always be accessed directly from the about menu page (the about page is the right-most option on the bottom menu).

## File permssions

There are different permissions needed, depending on Android OS version. Not all permissions are strictly needed, depending on your use case, but “Write to device storage” and “Manage all files” permissions are required for a sync to run correctly. “Manage all files” permission is only available on Android 11 and newer.

!!! info

    For FolderSync to be able to access all files it is necessary to grant permission to access “all files” not only “media files” which is a more restricted version of this permission. FolderSync does not know if “all files” or “media files” has been allowed, and if only “media files” is allowed some files can not be read, and FolderSync will assume those non-readable files and folders doesn’t exist (as they are not reported by the file system).

To grant access to Android/data folder on internal SD card FolderSync will open a permission chooser where the user must manually grant permission to access the folder. When opening permission chooser it should already be in the Android/data folder on version 3.1.0 and newer. If you need to access other folders under Android you can try navigate up one folder and grant permission to Android folder (and not Android/data) - this is not allowed on all devices though, but if possible will allow you to access all subfolders of the Android folder.

## Location background permssion

If you set allowed or disallowed Wi-Fi SSID names on FolderPair, FolderSync needs this permission to be able to read the name from Android. It is important the the permission granted is of the type "Allow always" in order to access Wi-Fi SSID name while running sync in background.

If you don't st SSID name filter you do not need to grant this permission.

## Battery optimization

For FolderSync to be able to run in the background to sync files, you will need to exempt the app from battery optimization. This is also required for FolderSync to be able to scehdule precise alarms for when a sync should run.
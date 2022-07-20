# Scheduleding

## Why don't my scheduled sync run?
There can be many reasons for this, most common that battery optimization is enabled for FolderSync (you will need to excluded it for scheduling to work properly). If you have the app installed on SD card, the scheduler will not be set on boot up of the device because of limitations in the Android OS. This is why FolderSync from version 1.7.0 on will have its install location set to "internalOnly". Otherwise it will mean scheduled syncs will not run until you have started FolderSync at least once.

Another reason can be that the connection type is not allowed for the folderpair that is scheduled to sync, or some other condition is not met. You can also try enabling "Use full wakelock" in settings - some devices require this setting to be enabled or they will not wake correctly.

## Battery optimization
Most common issue is that the Android OS is battery optimizing the FolderSync process so it cant run scheduled sync. To ensure sync can occur in background, disable any battery optimization for FolderSync in Android settings.

## WiFi SSID not detected
Scheduled sync can be broken if Wifi SSID is not detected and you configured a SSID filter on folderPair connection settings - if you need FolderSync to detect SSID, please allow it background access to location on newer versions of Android. If you already gave permission to only allow while app is in use, you have to go to Android app settings for FolderSync and give location permission again for background use. If you don't wan't to do that, remove SSID filter configuration on folderpair.

## Wifi doesn't turn on
Unfortunately Android no longer allows turning on WiFi for apps targeting Android 10.

## Instant sync issues
On Android 6.x/7.x instant sync functionality will not work for most devices for external SD card. This is an Android bug or perhaps a new undocumented limitation by Google. Nothing we can do about it unfortunately.
# Scheduleding issues

## Battery optimization
Most common issue is that the Android OS is battery optimizing the FolderSync process so it cant run scheduled sync. To ensure sync can occur in background, disable any battery optimization for FolderSync in Android settings.

## WiFi SSID not detected
Scheduled sync can be broken if Wifi SSID is not detected and you configured a SSID filter on folderPair connection settings - if you need FolderSync to detect SSID, please allow it background access to location on newer versions of Android. If you already gave permission to only allow while app is in use, you have to go to Android app settings for FolderSync and give location permission again for background use. If you don't wan't to do that, remove SSID filter configuration on folderpair.

## Wifi doesn't turn on
Unfortunately Android no longer allows turning on WiFi for apps targeting Android 10.

## Instant sync issues
On Android 6.x/7.x instant sync functionality will not work for most devices for external SD card. This is an Android bug or perhaps a new undocumented limitation by Google. Nothing we can do about it unfortunately.
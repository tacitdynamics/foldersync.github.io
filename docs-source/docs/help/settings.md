# Settings

The about and settings screens allows you to configure FolderSync and export/import configuration.

## On about screen

### Scheduled sync
You have a an option to disable scheduled syncs completely. In this case no scheduled syncs will run. Disable this if you want to use manual sync only or syncs initiated from Tasker/Locale.

### Notifications
There is also an option to disable notifications, overriding any notification setting configured on folderPairs. You can also on newer Android version configure Android notication configuration for different notication channels used.

FolderSync has 5 configured notification channels (on Android 8.0 or newer):

* **FolderSync Service** - notification shown when background sync is running
* **FolderSync File Manager** - notifications shown by the file manager
* **FolderSync Sync Success** - notification shown on sync success (if enabled on folderPair)
* **FolderSync Sync Changess** - notification shown on sync changes (if enabled on folderPair)
* **FolderSync Sync Errors** - notification shown on sync error (if enabled on folderPair)

### Access pin code
You can set a pincode and timeout if you want to protect access to the app.

## On settings screen

### General

* **Language** - set language. Normally FolderSync will follow device language setting.
* **Startup wizard** - rerun startup wizard.
* **Crash reporting** - Toogle crash reporting.
* **Google Analytics** - Toogle Google Analytics.
* **Notifications** - access Android notification settings for the app.

### User interface

* **Show bottom bar tab title** - Toggle showing titles on bottom menu bar.

### Internal storage

* **Root access** - Enable access on rooted device. Only needed to access files that would otherwise be inaccesible.
* **Temp folder** - configure the location of the temp folder. This should be on internal storage and is used by FolderSync to store temporary files during sync etc.

### Sync options

* **Disable stack notifications** - Toogle this if you don't want stacked notification styled.
* **Keep screen on** - Keep screen on while syncing. Only recommended as a possible solution if syncing in background is paused by the Android OS.
* **Retains sync logs** - The number of total sync logs to retain, FolderSync will automatically delete the oldest sync logs when this limit is hit.
* **Difference in milliseconds allowed when comparing files** - When comparing files during sync this is difference allowed when checking if files are identical.
* **Required free space** - The minimum space in MB that is required to be available on SD card when syncing files.

### Automation

* **Enable** - Enable automation if you want to enable automation using deeplinks.
* **Help** - Clicking the help entry gives a list of possible deeplinks that can trigger action. Deeplinks are specific to the specific install of FolderSync, as they contain a unique generated key.

### Backup

* **Backup folder** - configure the location of the backup folder. 
* **Backup database** - Used to export the underlying database of FolderSync. Backups can be encrypted using a password to protect your credentials.
* **Restore databse** - Restore a database backup. This will overwrite any existing folderPairs, accounts and sync history in the opened app. This will work between different versions of FolderSync. 

# Import configuration

When the end user opens the app and the app is able to find a configuration JSON file in a predfined location on internal storage, FolderSync will show an import wizard to the end user where they will be asked to login to any accounts found and enter any custom values specified in the account path. 

If credentials are in the config file or if the user has previously completed login for accounts found in the JSON file then no import wizard will be shown.

Only configuration created as part of on import can be updated/overwritten by a new import. Manually created accounts/folderPairs will not be touched (unless updateType in JSON is configured to use update type RemoveAllExisting, in which case everything will be deleted).

## Checking for updates
The app will check for a file each 12 hours (if running), and will then set to trigger the wizard on the next start if needed. File is always checked on a cold start of the app.


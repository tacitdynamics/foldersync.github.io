# Creating configuration

Before exporting a configuration file, accounts and folderPairs should be configured to exactly match what will end up on the end users devices. When exporting configuration later you can choose to omit login information so the end user will be asked for this on startup of the app.

## Accounts
The path field on account allows for 1 or more placeholders contained in double curly brackets, which the end-user will also be asked for on startup. For example you can specify the following account path:

`/webdav/{{User ID}}/some/path{{Company Name}}/`

The end user will then be asked to enter User ID and Company Name when attempting to login in the startup wizard, when this is shown on import, in addition to username and password.

Note:
When handing login on import wizard for the end user, the app will try to login for other accounts using the same server and account type, using the username and password provided. Ensure any account with placeholders configured are at the top of the list, if another account without placeholders can use the same account, so the end user has less hassle with entering credentials.

## FolderPairs
The local path field on folderPair allows for 1 placeholder contained in double curly brackets called ExternalSdCard which will transform to the users external SD card path on import. For example you can specify the following device path (remember forward slash after placeholder):

`{{ExternalSdCard}}/some/path`

This will then become something like this after import, if external SD card is found:

`/storage/6464-4544}/some/path`

## Export configuration JSON
To export the configuration file go to **About->Settings->Export Configuration** in the Business edition of foldersync. The JSON file will be written to the configured backup folder.

When exporting, the option to include credentials is not selected. It is not recommended to include credentials other than for testing or for manual import use.

There is also an update type which defaults to UpdateExisting. The options are described here:

* `UpdateExisting (default)`
Updates properties of any existing accounts/folderPairs by importKey, else it will add new entries, other accounts/folderPairs are untouched. Will not update folderPairs/accounts that have been configured manually.

* `OverwriteExisting`
Overwrites any existing accounts/folderPairs by importKey fully, else adds new entries, rest is untouched.

* `RemoveAllExisting`
Removes all existing accounts/folderPairs, import all in file as new. FolderSync will delete the config.json file after import.

* `AppendToExisting`
Don't touch existing accounts/folderPairs, import all as new.

## Editing the JSON file
The JSON export file contains a description field, which content is shown in wizard and you can put some helpful text and a link in there if you need to point users to an online help guide.

```
{
    "config": {
        "description": "Optional description goes here.",
        "updateType": "UpdateExisting"
    }
}
```


# Automation

FolderSync works as Tasker plugin and supports deeplinks when triggered from other automation apps. This means one or more folderpair syncs can be initiated or cancelled when a condition or rule you configured in automation app occurs.

## Tasker
Configuring an automation apps is out of the scope of this help text, but FolderSync is found in the the Plugin section for Tasker. Note that syncs will run no matter what settings they are configured with, when initiated from automation app, except if the allowed connection requirement(s) are not met.


## Deeplinks
FolderSync also supports triggering actions via deeplinks. To trigger a deeplink from Tasker use “Browse URL” action. For deeplinks to work automation must be enabled in Foldersync settings. 

Opening deeplinks by copy/pasting directly to browser will not work. The link has to be handled by the app to work, which will *not* happen when directly entering the link into a browsers address bar. 

!!! info

    For deeplink to work they have to be enabled on the settings screen.
    This will also make the Automation tab visible for folderPairs.

# Deploy configuration

Deployment of JSON configuration file should be handled by the MDM. Consult your MDM documentation for guidance to how it supports writing files to storage of managed devices.

When deploying the JSON file to end users, it should be put the internal storage folder which FolderSync will check. These JSON file locations are currently supported:

```<internalStr>/Android/data/dk.tacit.android.foldersync.app/files/import/config.json```
```<internalStr>/FolderSync/import/config.json```

Note the name of the file: ```config.json```



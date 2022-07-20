# Sync 

## How do I avoid conflicts when configuring a new folderpair where both folders already contains all the files?
If a file that has not been synced before by FolderSync, exists both locally and remote when syncing and the two corresponding files do not have an identical modified timestamp, then you will get a conflict error for the files. 
The same conflict will happen for a file that has been previously synced, when both the local and remote file has changed since last sync (both files get updated by your or another app with new timestamps and perhaps new content).

To eliminate this conflict when configuring a folderPair for the first time, and you KNOW the files are identical, you can set "FolderPair -> Sync option -> If both local and remote file are modified" option to "Assume files are identical". Only do this as a temporary thing for the first sync and only if you are 100% sure the files in both local and remote folder are indeed identical.

## Why does instant sync not work?
This feature works only for local files device. When enabled, local file changes will be detected in the device folder, and a immediate partial sync will be attempted if other folderpair conditions allow this, such as network settings. Some custom ROMs may not support this. Newer versions of Android may not support this feature on external SD cards, since it appears folder/file change events are not propogated to apps properly.

## What is the conflict setting and how does it work?
When syncing a conflict can occur when both the local and the remote file has been modified since the last sync. You then have four options: to skip the file, to use the newest file or to use either the local or the remote file.
A conflict gets detected when both the local and remote modified time stamp for the file has changed since last sync - FolderSync could then of course just use the newest file, but then what if you had made some changes to the "older" file, that you wanted to save?
A conflict will not be detected in cases where the modified time stamp is within the threshold for modified time stamp bug fix setting

## Why do files sometimes get transferred even if they haven't changes?
There is some kind of bug on some Android versions, where timestamps of files change independently of Foldersync, even if they haven't changed. It could be caused by media scanning the SD card, remounting or rebooting or perhaps issues with timezones but we do not know for sure. We don't have the problem on our test devices, and currently only a small subset of users have this problem.
We are looking into handling this issue using md5 checksum to see if local files have changed before they are synced again. Look for it in a future release.
If the timestamp of a remote file change, for whatever reason, even if the file is unchanged, then FolderSync will not be able to detect it and the file may be retransferrred.

## Why is there no overall sync progress shown?
FolderSync's current sync engine progresses through the folder structure of the remote and local folders as they sync runs, and process each folder on its own. FolderSync doesn't know how many sub folders and files that may remain to be synced in folders not yet processed. It is perhaps possible to list all files/folders before syncing of changed files starts, but it may still take a long time to calculate this because it can depend on 1000's of web requests for large folder structures, and when no files are synced, this is essentially what happens anyway.

Think about it like this: if you run a sync where no files are transferred, the time that the sync needs to run, is the same time as is needed to calculate the number files to be synced (if there had been any). So it doesn't make sense to show progress for syncs's where no files are transferred (because when the calculation is ready, the sync has completed). 

A future version of FolderSync may include a updated sync engine, where this calculation is done, and all files are transferred at the end of the sync. Then it will be possible to show how many file transfers remain in sync.

## When are modification timestamps for files updated?
Generally modified time stamp for a file is set on download and upload, not at any other time. However not all cloud providers or protocols support setting modified time stamp of uploaded files, so images that is uploaded may get a newer modified time stamp than on the device etc.. 
This table will illustrate which providers and protocols support setting the modification time stamp for an uploaded file:

|Provider/protocol |	Modification time stamp preserved
------------- | -------------
Amazon S3	|    No
Box	        |    No
Dropbox	    |    No
FTP	        |    Yes (if supported by server)
Google Docs	|    No
Google Drive |	Yes
NetDocuments |	No
SFTP	    |    Yes (if supported by server)
OneDrive	|    No
SMB/Cifs	|    Yes (if supported by server)
SugarSync	|    No
Ubuntu One	|    No
WebDAV	    |    No

## Why are my files not being synced correctly?
This answer will try to address a range of common reasons why your files may not sync as you thought they would:

If subfolders or some files are not syncing at all - make sure sync of subfolders is enabled. Also check if the files or folders not marked as hidden (in Google Docs this will happen if you choose to hide items from being shown in "home"). If so, enable sync of hidden files. Also make sure items are not excluded because of a sync filter.

Connections - make sure the allowed connection type is enabled at the time the sync should run or else the folderpair will not be synced at all.

FTP/FTPES - if you have problems with FTP syncing, please try the legacy option first before contacting support.

Special characters in file names - please use universal acceptable file characters in file and folder names. Some good recommendations can be found here: http://www.mtu.edu/umc/services/web/resources/cms/characters-to-avoid.html
Box doesn't accept file names or folders that start with a dot ".".

## FolderSync doesn't delete removed files in a two-way sync. Why?
FolderSync has a fairly simple sync engine, meaning that FolderSync doesn't store state for each individual file. Thus the only information it knows about a file is what it knows at the time of the sync. Thus, if you delete a previously synced file for a two-way sync folderpair on either the local or remote end, this file will be resynced, because FolderSync sees this a an unsynced file. This is intentional.

Note: From version 1.4.0 on FolderSync support deletions in two-way sync.

## FolderSync overwrite changes in my local/remote file and uses the oldest file?
This can only happen if the rule "overwrite always" is used, or if you are experiencing the Android OS bug mentioned in the next question. If "overwrite always" is not set, FolderSync will never overwrite the newest file - but the bug mentioned results in the newest file having an older timestamp. See below for more details.

## FolderSync sometimes sync files that haven't changed. Why?
FolderSync compares the lastmodified timestamps on the local and the remote file when the option to overwrite older files in a folderpair is set. If the targetfile is older, it is overwritten by the sourcefile. AmazonS3 and Dropbox don't have any support for setting the timestamps of uploaded files, so when a file is uploaded to one of these services, FolderSync attempts to set the timestamp on the local file, to ensure the timestamps are in sync.

Likewise when a file is downloaded, the timestamp of the localfile is set to that of the file in Dropbox or Amazon S3. This ensures, that on the next sync check FolderSync will see the files as identical.

However, on some Android devices there is a bug in the operating system that makes setting the timestamp of the local file fail. Thus, at the next sync check, typcially when using two-way sync, FolderSync sees that the cloud and local file have different timestamps, and thus syncs the file again. This will then happen every time.

From version 1.4.0 on the local and remote timestamp are stored in a database, and used for comparison at next sync. Along with an user configurable option to to ignore a timestamp difference, this should eliminate the resyncing problem.

For information regarding the Android OS bug see these references:
http://code.google.com/p/android/issues/detail?id=15480
http://code.google.com/p/android/issues/detail?id=1699

Even the official Dropbox app has the same problem:
http://forums.dropbox.com/topic.php?id=22437


## Sync failing because of file conflicts
If a file that has not been synced before, exists both locally and remote when syncing, and the two corresponding files do not have an identical modified timestamp, you will get a conflict. The same conflict will happen for a file that has been previously synced, if both the local and remote file changes since last sync (gets updated with a new timestamp and perhaps new content, by other applications or you). You can configure the folderpair to use the overwrite oldest file in such a case using the conflict setting under FolderPair->Advanced. The remote and local file may be identical, other than the timestamp, but FolderSync can not verify this without overwriting one of them with the other, since a file-hash of the remote file is often not available. 

## Bad request errors or failing folderpairs
Please try to re-authenticate account. In some cases you also need to re-select to remote folder for folderpairs, since the path structure on the remote end has changed because of usages of new API versions. Just re-select the folder you are already using, so the remote folder info can be refreshed.

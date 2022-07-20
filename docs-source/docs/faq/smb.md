# SMB

## How to connnect to SMB?
Please ensure you are using correct protocol SMB1, SMB2 or SMB3. SMB1 is deprecated and not by default enabled in many newer OS versions etc. FolderSync uses jcifs for SMB1 and smbj for SMB2/3 and should be compaible with all SMB server that work with these libraries.

For SMB2/3 ensure share name is entered correctly. FolderSync does not have the ability to browse shares, so the share name must be configured correctly for connection to succeed.

## Error when connecting to SMB (Samba) on linux or NAS?
FolderSync uses the smbj library for SMB access. If you are connecting to Samba server (used by many NAS also) and you are connecting without username/password, it may cause issues. Please ensure a username/password is provided.

## Syncing files ending with dot (.) fails when uploading to SMB server?
Unfortunately this is an issue with many SMB servers and/or widows, they do not accept files ending with dot. 
The issue is not the missing extension, but the ending dot.
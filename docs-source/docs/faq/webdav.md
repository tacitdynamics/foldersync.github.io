# WebDAV 

## 2FA access for NextCloud?
To login on server with 2FA enabled you need to generate App Password / Token for your user, this password can then be used in FolderSync to login.

See this article: 
[https://help.nextcloud.com/t/how-to-connect-to-webdav-using-totp/7036/2](https://help.nextcloud.com/t/how-to-connect-to-webdav-using-totp/7036/2)

## I can not connect to a non-HTTPS WebDav server. Why?
Because of security restrictions when targeting newer Android SDK's non-SSL http communication is no longer allowed by default and will not be readded, as it would be a security risk for all users of the app, since it can enable man-in-the-middle attacks on compromised networks. This can not be configured as a user setting because of the way it configured in the app.

It is recommended you enable SSL on your server or NAS, using the default self-signed SSL certificate it most likely has configured. FolderSync support self-signed certificates which can be enabled on account. If you absolutely have no other choice but to use a non-SSL server, please contact support to request the 2.9.x version FolderSync. Note, this old version is unsupported and will never receive updates.

## Upload fails with java.io.IOException: Stream Closed or similar?
Some servers has a very low request time out setting. If you are using Apache webserver, many NAS like Synology or MyCloud are, you can remove usage of LoadModule reqtimeout_module modules/mod_reqtimeout.so in apache conf file.

## OwnCloud connection issues?
May be caused by streamlining of the configuration into two account types for ownCloud 6/7 and 8 respectively. Please reconfigure your accounts accordingly. If you get something like "refused stream" error for HTTP/2 you need to upgrade to latest nginx web server and version 2.9.4, where this is fixed.

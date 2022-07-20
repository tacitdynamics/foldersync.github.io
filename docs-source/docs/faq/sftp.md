# SFTP

## I can not login to my SFTP server
FolderSync uses the sshj library for SFTP. Please ensure your server algorithms are supported and key files are supported.

[https://github.com/hierynomus/sshj](https://github.com/hierynomus/sshj)

## I get a "Received message is too long: 1416128878" error with SFTP. Why? 
This seems to be a problem with the server. It responds with something the FolderSync doesn't understand. See detailed answer below:

When I try to use sftp or scp2, I get a message like this: 
Received message too long (or "Bad packet length") 1416586337 
and the connection fails. What's wrong? 

"In order for this to work, the SSH session must be "clean" — that is, it must have on it only information transmitted by the programs at either end. What often happens, though, is that there are statements in either the system or per-user shell startup files on the server (.bashrc,.profile,/etc/csh.cshrc,.login, etc.) which output text messages on login, intended to be read by humans (likefortune,echo "Hi there!", etc.). Such code should only produce output on interactive logins, when there is a tty attached to standard input. If it does not make this test, it will insert these text messages where they don't belong: in this case, polluting the protocol stream between scp2/sftp and sftp-server. The first four bytes of the text gets interpreted as a 32-bit packet length, which will usually be a wildly large number, provoking the error message above"

Taken from here: http://www.snailbook.com/faq/sftp-corruption.auto.html

So you need to modify the SFTP server in some way, so that it doesn't send back plain text.

## Login with private key file doesnt work
Please ensure file is in one of the following formats: pkcs5, pkcs8, openssh-key-v1, ssh-rsa-cert-v01@openssh.com, ssh-dsa-cert-v01@openssh.com
---
layout: post
title:  "Enable php on mac"
date:   2014-08-24 21:07:00
categories: ios

---
[link](http://osxfactor.com/2009/08/30/how-to-enable-php-mysql-in-snow-leopard/)

1. Navigate to `/etc/apache2`
2. Do a search for “php”. You should see the following line:`#LoadModule php5_module        libexec/apache2/libphp5.so`Remove the “#”
3. Save the file. You may need to authenticate upon saving.
4. run `sudo apachectl restart` to restart apache
5. visit `localhost` you will see **It works!**
6. `/etc/apache2/httpd.conf`Search for “virtual” in your text editor. You should see the following lines:

```
#Virtual hosts
#Include /private/etc/apache2/	extra/httpd-
```
Uncomment the second line that starts with “#Include” by removing the “#”. We now need to modify httpd-vhosts.conf file to add our virtual hosts.

7. open`/etc/apache2/extra/httpd-vhosts.conf`

```
DocumentRoot "/Users/username/Sites/Website"
ServerName yourwebsitename
```

### Another tutorial
* Install : XAMPP Mac OS X 1.7.3 [download](http://www.apachefriends.org/download.php?xampp-macosx-1.7.3.dmg)
* `sudo su`
* `/Applications/XAMPP/xamppfiles/xampp start`

if you see 

```
XAMPP: Starting ProFTPD.../Applications/XAMPP/xamppfiles/xampp: line 184: /Applications/XAMPP/xamppfiles//var/proftpd/start.err: No such file or directory fail.  
Contents of "/Applications/XAMPP/xamppfiles//var/proftpd/start.err":  		cat: /Applications/XAMPP/xamppfiles//var/proftpd/start.err: No such file or directory  
```
do these commands

```
	`sudo mkdir /Applications/XAMPP/xamppfiles/var/proftpd/`
	
	`touch /Applications/XAMPP/xamppfiles/var/proftpd/start.err`
	
	`sudo /Applications/XAMPP/xamppfiles/xampp fix_rights`
	
	then redo the `/Applications/XAMPP/xamppfiles/xampp start` cmd
```

* in http://localhost you can see the test site

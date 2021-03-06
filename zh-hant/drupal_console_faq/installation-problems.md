# Installation problems 

When you run DrupalConsole from your Drupal 8 root directory, you can get different error messages, we will try to compile the reported issues and how to have them fixed.

--- 

### Error message:
```
[PDOException] SQLSTATE[HY000] [2002] No such file or directory
```
You will need to edit your 'host' in your 'settings.php' file. 

Navigate to `sites/default/settings.php`. In your `settings.php` file, change the `host` to read:
```
'host' => '127.0.0.1'
```
or if your 'settings.php' file already reads:
```
'host' => '127.0.0.1'
```
change it to read:
```
'host' => 'localhost'. 
```
After you make the change, be sure to save the file and then run DrupalConsole again.

---

### Error message:
```
[PDOException]
SQLSTATE[HY000] [2002] Can't connect to local MySQL server through socket '/tmp/mysql.sock'
```
Creating a symlink pointing to `/tmp/mysql.sock`:
```
ln -s /path/to/your/mysql/data/mysql.sock /tmp/mysql.sock
```

---

### Error message:
```
Fatal error: require(): Failed opening required 'drupal.php'
```
This can be caused by the ioncube loader extension, which can be used to encode
and decode PHP files. This extension prevents normal working of any phar files
with require/include calls. You must disable the extension.

---

### Warning message:
```
The configuration date.timezone was missing and overwritten with America/Tijuana.
```
Your timezone is not set in php.ini; you must correct this by editing the appropriate php.ini for the command line (there's a separate php.ini for the CLI). 

Run `php --ini`and look for "Loaded Configuration File". For example, in Ubuntu: 
```
Loaded Configuration File:         /etc/php5/cli/php.ini
```
Edit that file and look for 
```
;date.timezone =
```
Uncomment this line and assign the desired timezone as seen on http://php.net/manual/en/timezones.php. 

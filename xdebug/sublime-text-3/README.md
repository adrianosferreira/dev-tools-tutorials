#Xdebug for Sublime Text 3
This tutorial was based upon: http://www.sitepoint.com/debugging-xdebug-sublime-text-3/

##Installing and Setting up Xdebug PHP extension
First of all check whether Xdebug is installed in the machine, that can be done through the phpinfo(), for instance. There should be a section dedicated for Xdebug.

###Enabling Xdebug on MAMP
Fortunately Xdebug comes natively on MAMP through a Zend extension and it's pretty straightforward to enable it:
* Open the php.ini file accordingly the PHP version that you are running: **MAMP/bin/php/php5.6.2/conf/php.ini**
* Scroll down and uncomment the zend_extension for xdebug line:
```
[xdebug]
zend_extension="/Applications/MAMP/bin/php/php5.6.2/lib/php/extensions/no-debug-non-zts-20131226/xdebug.so"
```
* Now add a few parameters:
```
[xdebug]
zend_extension="/Applications/MAMP/bin/php/php5.6.2/lib/php/extensions/no-debug-non-zts-20131226/xdebug.so"
xdebug.remote_enable=1
xdebug.remote_handler=dbgp
xdebug.remote_host=127.0.0.1
xdebug.remote_port=9000
xdebug.remote_log="/var/log/xdebug/xdebug.log"
```
* Save the file and close

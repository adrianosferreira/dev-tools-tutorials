#Xdebug for Sublime Text 3
This tutorial was based upon: http://www.sitepoint.com/debugging-xdebug-sublime-text-3/

##Installing and Setting up Xdebug PHP extension
First of all you will need to check whether Xdebug is installed on your machine, you can quickly check that with phpinfo(). There should be a section dedicated for Xdebug.

In case it's not there, you should install it first. I won't go in details about this installation, there are lots of materials in the internet about it and also it will depend upon the tool you are using to run PHP on your machine

In my case I have MAMP free and it's pretty straightforward to configure it:

* Open the file **MAMP/bin/php/php5.6.2/conf/php.ini**
* Scroll down and uncomment the zend_extension for xdebug:
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

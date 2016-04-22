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

##Setting up Sublime Text 3
* Install Package Control on Sublime Text 3 if you haven't - https://packagecontrol.io/installation - just copy the text below and paste it on Console **View > Show Console**, then press ENTER
```
import urllib.request,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```
* Package installed now it's time to install the xdebug client package for Sublime
* Open the **Command Palette** in **Tools > Command Palette**
* Type "Package Install" and press **ENTER**
* Type "xdebug client" and press **ENTER**

##Setting up the Sublime Project
* Open a new file on Sublime and create a new project **Project > Save Project As**
* Now open the saved project file **.sublime-project** and add the parameters below (replacing with the right data):
```
{
	"folders":
	[
		{
			"path": "/Applications/MAMP/htdocs/my-project"
		},
		{
			"path": "/Applications/MAMP/bin"
		}
	],
	"settings":
	{
		"xdebug":
		{
			"url": "http://localhost:8888/my-project/",
			"break_on_exception": false,
			"max_depth": 1024,
			"max_children": 9999
		}
	}
}
```

##Interesting Notes
* If you don't set "break_on_exception" as false, your breakpoints won't work well. Xdebug will then stop on each exception, you will feel that your breakpoints are being ignored.
* The "max_depth" and "max_children" are very important, the default values are too small. So if you don't increase them you won't be able to have a full view of your variables.

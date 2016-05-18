#MongoDB on OS X

##Installing MongoDB Community Edition Manually##

* Download the binary files in: https://www.mongodb.org/downloads
* Create a new folder where you want to install MongoDB and extract the binary files over there
* Add the binary files location at the $PATH variable, example:
```
export PATH=$PATH:~/mongodb/bin
```
* Create the data folder in **/data/db** as root:
```
sudo mkdir -p /data/db
```
* Add some permissions to the database folder:
```
sudo chmod 0755 /data/db
sudo chown -R mongod:mongod /data/db
```
###Notes###

MongoDB also has an option where you can create the data directory in another location, but that's generally not a good idea, because it just slightly complicates things such as DB recovery, because you always have to specify the db-path manually. I wouldn't recommend doing that.

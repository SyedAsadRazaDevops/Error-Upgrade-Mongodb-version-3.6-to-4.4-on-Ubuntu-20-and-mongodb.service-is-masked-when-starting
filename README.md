# Upgrade Mongodb version 3.6 to 4.4 on Ubuntu 20 LTS and mongodb.service is Unmasked when starting

# upgrading mongodb from 3.6 to 4.0
```
sudo apt list --installed | grep mongodb
```
```
sudo systemctl stop mongod
```
```
wget -qO - https://www.mongodb.org/static/pgp/server-4.0.asc | sudo apt-key add -
```
```
echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list
```

>Important part:
```
sudo apt-get update && sudo apt-get install -y mongodb-org=4.0.14 mongodb-org-server=4.0.14 
```
sudo systemctl start mongod
```
mongo -version
```
>MongoDB shell version v4.0.14

```
mongod -version
```
>db version v4.0.14

That worked for me, I hope it will for you too :)

# Uninstall mongoDB from ubuntu

In response, I want to remove MongoDB 3.6 and install MongoDB 4.4.

I tried the following commands:
```
 apt-get remove --purge mongodb
```
and also
```
apt-get autoremove --purge mongodb
```

# How To Install MongoDB 4.4 on Ubuntu 20.04

To start, import the public GPG key for the latest stable version of MongoDB by running the following command. If you intend to use a version of MongoDB other than 4.4, be sure to change 4.4 in the URL portion of this command to align with the version you want to install:
```
curl -fsSL https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
```

Run the following command, which creates a file in the sources.list.d directory named mongodb-org-4.4.list. The only content in this file is a single line reading 
```
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
```

After running this command, update your server’s local package index so APT knows where to find the mongodb-org package:
```
sudo apt update
```
```
sudo apt install mongodb-org
```
# Starting the MongoDB Service and Testing the Database

```
sudo systemctl start mongod.service
```
```
sudo systemctl status mongod
```

After confirming that the service is running as expected, enable the MongoDB service to start up at boot:
```
sudo systemctl enable mongod
```


thankyou for reading!

Visit: https://askubuntu.com/questions/919108/error-unit-mongodb-service-is-masked-when-starting-mongodb
Visit: https://serverfault.com/questions/970628/upgrading-mongodb-from-3-6-to-4-0
Visit: https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-ubuntu-20-04



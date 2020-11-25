Instructions

Clone starter code
Add the following commands to the provisioning file
sudo apt-get update
sudo apt-get install nginx -y
To install MongoDB, add the following commands to the provisioning file.
# Import the public key
wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -
# Create a list file for MongoDB
echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list
# Reload package database
sudo apt-get update
# Install MongoDB - version 3.2.20 to pass tests
sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20
Inside the virtual machine, run the following commands to ensure the database is running correctly:
# Start MongoDB
sudo systemctl start mongod

# Check the status of MongoDB
sudo systemctl status mongod

# Enable MongoDB
sudo systemctl enable mongod

# Stop MongoDB
sudo systemctl stop mongod
Open the mongod.conf file to allow it to listen on port 0.0.0.0
sudo nano /etc/mongod.conf
Edit the bind ip to 0.0.0.0
Restart mongod and start mongo
sudo service mongod restart
sudo systemctl enable mongod
mongo
Run tests
cd tests
rake spec

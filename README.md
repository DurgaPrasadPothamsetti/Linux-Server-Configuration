# Linux-Server-Configuration(Udacity FullStack Course)
## About This Project
  This is the 5 th project in udacity full stack course.In this project We have to deploy one of our project to an instance using  a Linux server instance called [Amazon Lightsail](https://lightsail.aws.amazon.com/ls/webapp/home/instances)

### My Server Information
Server IP Address 13.127.166.26

Hosted Web Application URL [Click Here](http://13.127.166.26.xip.io/)

Grader Password
```
unix
```
grader key
```
-----BEGIN RSA PRIVATE KEY-----
MIIEpQIBAAKCAQEAwmcFopS+Z8a4lf+suqyd+NiYyCVG9nZmoHfrqrNCoue3Ba/A
u0nkKSwo7jzvpsIio11ZP3brW8ScMkBiylIvIM/OqcTBrh7BDt5udHtu9hn5dVu5
MWflVy8iUdeRvpL2D117Jx9kwnZ1EYPZkVyizHN8933wdsv45zdE4sNsucZnRKRs
PcmxXUoyUt+wWaGSjnzcHimgBKPsxyMRz4wwnAi1XGnc7Ox4DTS1Eh1ocV6gZHjj
u6Pek94F8rjB8qYZH4FqZqlEW8VDlCPxK8aiQkVtAW+TWZU6/N1kixOrkajSYfui
n0Of4SC35pOCc3Epu5g1t73lu7Jrggl3yjVK9QIDAQABAoIBACXWj445jWX9k+f+
P8yF1Kme3v31434NRaRuMvyir5GtsD33G3hYxYQOCFl2mt7GYp+Rh9GGgAD4n75Y
MeJXZLzqNbtthJUzfzg5qx4Y+FwGajuhgsZPBqCVmAR+BOwnBqWu+E2BGseO7vJd
y3czpKxOvkAdzzQQN34pj8rjZsIxuPPnJJp4l2y9J/GuJ/J5UvpLRYkNc1Lue6mw
FLx1ocJHhUcZEYZBXGDMXx5wzqKzZWuzB8vPyNsFWpYeCtjHFVwO0XcIg64LkGll
BJyA1Jyb14WSLFTIfI8ztkqJKS7fDIEW4/zyH/2ICw3JPuGlYoBQnAAXnl5ajuxG
Y80imnECgYEA6Mxra4rx47lFlNqHJJr6UmrxKhjQ55l7MZhT427PMLWSl/My+YyG
jm2yzpBQ9FTewIw5jGDBYhBSwKTu2Z8RvzAwusKruGzbcyH2pZF+A1t1/B5CSUbN
oa7w/+FI10Tdjp130nhuTRrMw6SKCjmfNYIqPo5VHx6+5OaNFmW6di8CgYEA1cb4
sQhQGVBwaXmCBBDUk8tG+4wR6NE73XUOT0e5lWA23cem8OBhXUHj/9FahThQgldl
Pdm6p/eUJirbJcLiLRPq3Zn/GQHLGXpWHZLzGr0OxqyOJO0xsltS9Lalv1jpOF2c
/4SNnj2ylnV85J7h2H65vVlXd5T8QBF3FKiBbBsCgYEAn0wKEVvRa19CwrnKEf1O
Xwk4nvK+OExo5SXz+UPA2PbWKc3LysEi7eEYoopUKuzMQ/twAaPPkDfVOGdj3Vwg
u6/RGGrPMHKks6LA8Mie7tMt5+gYuaWOXh2kYaOZwVwpM0aDUG0CJRa6mQFFR/vn
+qhoGcgxbQsP2vf8ASB5OBcCgYEAucKwD4VdtOGFDOIc7FODpPmasLLCTUCjeIhi
6tk0lmyIwKbglackc9jxujW9Js4Mh3ZR7zDnVVV5UsEitOlniCwqhm1ukdhRF86K
TiCHRtDJqjH/Qm8qJAXfS+36kQ89eVE/P3l7ZenO6Zcl87NsJKfZ1oNv0eWQXEvQ
4g6ah8kCgYEA2y6ZirlxDnd7JdIIiwPzKW3srWbs+n3EU6kLT4cX7/fVKMFW7kRI
72yIZWOuGcK/GC4jloom6pisSbROFooOjWiW82PATpGkGKECcUwJSBwEmU32vimG
tt5mlO9nEn71JA2sIWdchm6A/yB1Md1OG95FhVhTHZlh+s7LwnmIfz8=
-----END RSA PRIVATE KEY-----
```


### Steps To Connect As a grader:
  Save The Private Key Provided in Your Local Machine and Run the Following Command in Terminal
  ```
  ssh -i pathto/key -p 2200 grader@13.127.166.26
  ```
##Summary
1. Launch your Virtual Machine
2. Follow the instructions provided to SSH into your server
3. Create a new user  grader
4. Give grader permission to sudo
5. Update all installed packages
6. Change the SSH port from 22 to 2200
7. Configure the Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123)
8. Configure the local timezone to UTC
9. Install and configure Apache to serve a Python mod_wsgi application
10. Install and configure PostgreSQL
11. Do not allow remote connections.
12. Install git and clone  your Catalog App project (from your GitHub repository ) so that it functions correctly when visiting your server’s IP address in a browser.
### Configuring The Linux Server

#### Update all the packages
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

#### Create New User 'grader' :
  ```
  sudo adduser grader
  ```
  New User Will be Added
  ```
  sudo nano /etc/sudoers
  ```
  Below the root user Add this line to grant sudo permission to grader
  ```
  grader  ALL=(ALL:ALL) ALL
  ```
  
  #### Create SSH Key Pair:
   On Your Local Computer Open New Terminal and type following command
   ```
   ssh-keygen
   ```
   It Will Generate Private and Public Keys and Saved To .ssh Folder
   
   Then on your VM change to Newly created user
   ```
   su - grader
   ```
   Now Create a New Directory named .ssh
   ```
   mkdir .ssh
   ```
   Create a New File Named authorized_keys
   ```
   sudo nano .ssh/authorized_keys
   ```
   Go to .ssh Folder and open .pub extension file and copy it
   Paste it in authorized_keys 
   ```
   Give Permissions
   chmod 700 .ssh
   chmod 644 .ssh/authorized_keys
   ```
   Now Restart SSH server using following command
   ```
   service ssh restart
   ```
   
   Now Log into grader using private generated 
   ```
   ssh -i .ssh/id_rsa grader@ipaddress 
   ```
  #### Change Port Number From 22 to 2200
   Go to sshd config file using this command
   ```
   sudo nano /etc/ssh/sshd_config
   ```
   Locate port number and change it from 22 to 2200
   Press CTRL+X and Y to exit
   Restart again the ssh server using this command
   
   ```
   service ssh restart
   ```
   
   >Note: Before logging in add new ssh key with Custom,TCP,Portnum:2200 In Networking Tab In Amazon Lightsail Instance  
   
   After creating You can login using following command
   ```
   ssh -i .ssh/id_rsa -p 2200 grader@ipaddress
   ```
   
  #### Disable SSH login as root
  ```
  sudo nano /etc/ssh/sshd_config
  ```

  Change the  `PermitRootLogin no`
  
  #### Configuring ufw firewall
  ```
  sudo ufw allow 2200/tcp
  ```
  ```
  sudo ufw allow 80/tcp
  ```
  ```
  sudo ufw allow 123/udp
  ```
  ```
  sudo ufw enable
  ```
  It Allows all required ports
  
  Now Type this command to check allowed ports 
  ```
  sudo ufw status
  ```
  
  #### Change the time zone
  Change timezone using following command
  ```
  sudo dpkg-reconfigure tzdata
  ```
  
  Select 'None of the Above' and select UTC
  
  #### Install Apache2 Server
  Go to Terminal and type
  
  ```
  sudo apt-get install apache2
  ```
  
  And Then mod_wsgi
  
  ```
  sudo apt-get install python-setuptools libapache2-mod-wsgi
  ```
  
  Now Enable mod_wsgi
  
  ```
  sudo a2enmod wsgi
  ```
  ##### Setup Your Flask App with Apache2
   Creating a Flask App
   Go to /var/www/ directory
   ```
   cd /var/www/
   ```
   
   Then Create a New Folder Named FlaskApp

     ```
    sudo mkdir FlaskApp
     ```
   
   Now Install Git
   
   ```
   sudo apt-get install git
   ```
   
   Go to the FlaskApp 
   ```
   cd FlaskApp
   ```
   Now Clone Your Repository Here
  
   
   ```
   sudo git clone https://github.com/username/catalog.git
   ```
   
   Rename Your Repository Name as FlaskApp

   
   Then Rename Your project main file to `__init__.py`
   Now Use following code instead of secret_client.json  in the script due to error while accessing json
   ```
   PROJECT_ROOT = os.path.realpath(os.path.dirname(__file__))
   json_url = os.path.join(PROJECT_ROOT, 'client_secrets.json')
   ```

   Reffered from [stack overflow](https://stackoverflow.com/questions/44742566/wsgi-cant-find-file-in-same-directory-in-app)
   
  ##### Install Postgres
   Install Postgres
   ```
   sudo apt-get install postgresql
   ```
   
   Now type

   ```
   sudo su - postgres
   ```

   postgres shell 
   ```
   psql
   ```
   
   create user 
   ```
   CREATE USER catalog WITH PASSWORD 'password';
   ```
   
   Give Permission 
   ```
   ALTER USER catalog CREATEDB;
   ```
   
   Create a Database using name Catalog
   ```
   CREATE DATABASE catalog WITH OWNER catalog;
   ```
   
   connect to Database
   ```
   \c catalog
   ```
   
   Revoke all permissions 
   ```
   REVOKE ALL ON SCHEMA public FROM public;
   ```
   
   Give schema permission to user catalog 
   ```
   GRANT ALL ON SCHEMA public TO catalog;
   ```
   
   exit  
   ```
   \q and exit
   ```
   
   Change the database connection in both `database_setup.py` and `__init__.py` as `engine = create_engine('postgresql://catalog:password@localhost/catalog')`

  #### Enable New Virtual Host
   `sudo nano /etc/apache2/sites-available/FlaskApp.conf`
   
   Paste This code
   ```
   <VirtualHost *:80>
		ServerName yourstaticip.xip.io
		ServerAdmin admin@mywebsite.com
		WSGIScriptAlias / /var/www/FlaskApp/flaskapp.wsgi
		<Directory /var/www/FlaskApp/FlaskApp/>
			Order allow,deny
			Allow from all
		</Directory>
		Alias /static /var/www/FlaskApp/FlaskApp/static
		<Directory /var/www/FlaskApp/FlaskApp/static/>
			Order allow,deny
			Allow from all
		</Directory>
		ErrorLog ${APACHE_LOG_DIR}/error.log
		LogLevel warn
		CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
   ```
   Enable  virtual host 
   `sudo a2ensite FlaskApp`
   
   Disabling Default page
   `sudo a2dissite 000-default.conf`
   
  #### Create .wsgi file
    ```
    cd /var/www/FlaskApp
    sudo nano flaskapp.wsgi 
    ```
   Paste the following code 
   
   ```
   #!/usr/bin/python
    import sys
    import logging
    logging.basicConfig(stream=sys.stderr)
    sys.path.insert(0,"/var/www/FlaskApp/")

    from FlaskApp import app as application
    application.secret_key = 'Add your secret key'
   ```
   save and exit
   
   This one is reffered from [Digital ocean](https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps)
   
   #### Installing requirements

   ` pip install flask sqlalchemy psycopg2 requests oauth2client`
   
   #### Setup google oauth2
   Login to your [developer console](https://console.developers.google.com) and select your project and edit OAuth details as following
   
   Javascript origin url
   `http://yourstaticip.xip.io`
   
   redirect URI
   
   `http://yourstaticip.xip.io\login`
   
   `http://yourstaticip.xip.io\gconnect`
   
   `http://yourstaticip.xip.io\callback`
   
   xip.io is a free DNS which will be the same as using IP address
   
   #### And Now 
   Restart your apache2

   ```
   sudo service apache2 restart
   ```
   ##Third Party Resources
   [developer console](https://console.developers.google.com)
   [Digital ocean](https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps)
   [stack overflow](https://stackoverflow.com/questions/44742566/wsgi-cant-find-file-in-same-directory-in-app)
   
   

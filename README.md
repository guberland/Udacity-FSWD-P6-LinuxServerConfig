# P6_Linux Server Configuration

This is the sixth Undacity Full Stack Nanodegree project, this project creates
a secured Linux server and host Item Catalog project on it.

## Server
  IP address: 35.162.168.226 
  
  SSH port:2200
  
  Project portal: http://35.162.168.226/main/category/
## Setup
### Update currently installed packages
  1. `sudo apt-get update`
  
  2. `sudo apt-get upgrade`
  
### Create user grader
  1. create grader with command `sudo adduser grader` 
  2. give grader sudo permission with command `sudo nano /etc/sudoers.d/grader` and copy in 
  `grader ALL=(ALL:ALL) ALL`  
  3. on your local machine type ssh-keygen and paste the pub file into grader/.ssh/authorized_keys  
  4. change owner of .ssh and authorized_keys to grader and permission to 700 and 644 respectively
  5. open ssh config file by sudo nano /etc/ssh/sshd_config and change the following:             
      -Port 22 to 2200
      -`PermitRootLogin no`
      -`PasswordAuthentication no`  
### Uncomplicated Firewall/NTP Configuration  
   - allow SSH on port 2200         `sudo ufw allow 2200/tcp`
   
   - allow HTTP on port 80          `sudo ufw allow 80/tcp`
   
   - allow NTP on port 123          `sudo ufw allow 123/udp`
   
   - enable firewall                `sudo ufw enable`
   
   - install NTP                   `sudo apt-get install ntp`
   
   __make sure you test your private key before proceeding by typing                                                                         `ssh grader@35.162.168.226 -p2200 -i .ssh/PRIVATEKEY`__
   
### Apache2 Configuration
  1. install Apache `sudo apt-get install apache2`
  
  2. `sudo apt-get install python-setuptools libapache2-mod-wsgi`
  
### Flask 
   follow the guide and make change accordingly to suit your environment
https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps

### Git
  1. instasll Git                  `sudo apt-get install git`
  
  2. clone the Item Catalog project to the folder created during Flask setup mentioned above from digitalocean
  
### PostgreSQL
  1. install PostgreSQL            `sudo apt-get install postgresql` 
  
  2. change user to postgres       `sudo -su postgres and then psql`
  
  3. create user catalog           `sudo -u postgres createuser -P catalog`
  
  4. create databse catalog        `sudo -u postgres createdb -O catalog catalog`
  
  5. double check the created DB      `\c catalog` and `\dt` to see tables in catalog database
  
### MISC
  - you need to change client_secrets.json and provide full path of your directory
  
  - you also need to add the server IP on Google developer console under "Authorized JavaScript origins"
  
  - change `engine = create_engine('sqlite:///itemCatelog.db')` to `postgresql://catalog:PASSWORD@localhost/catalog`

### Authors

Chao Jiang

## Acknowledgments
-Udacity and its Forum, stackoverflow.com, digitalocean.com

-League of Legend/Dota item description

-background image



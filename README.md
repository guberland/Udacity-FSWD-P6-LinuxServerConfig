# P6_Linux Server Configuration

This is the sixth Undacity Full Stack Nanodegree project, this project creates
a secured Linux server and host Item Catalog project on it.

## Server
  IP address: 35.162.168.226 
  
  SSH port:2200
  
  Project portal: http://35.162.168.226/main/category/
## Setup
### Update currently installed packages
  1. sudo apt-get update
  
  2. sudo apt-get upgrade
  
### Create user grader
  1. create grader with command sudo adduser grader 
  2. give grader sudo permission with command sudo nano /etc/sudoers.d/grader and copy in 
  grader ALL=(ALL:ALL) ALL  
  3. on your local machine type ssh-keygen and paste the pub file into grader/.ssh/authorized_keys  
  4. change owner of .ssh and authorized_keys to grader and permission to 700 and 644 respectively
  5. make sure you test your private key before proceeding by typing 
  ssh grader@35.162.168.226 -p2200 -i .ssh/PRIVATEKEY
## Authors

Chao Jiang

## Acknowledgments
-Udacity and its Forum, stackoverflow.com



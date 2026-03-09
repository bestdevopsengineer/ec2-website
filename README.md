# ec2-website

#!/bin/bash
yum -y update
yum -y install httpd php
chkconfig httpd on
wget https://github.com/gr3yw01f/ec2-website/raw/master/phpapp.zip
unzip phpapp.zip -d /var/www/html/
service httpd start

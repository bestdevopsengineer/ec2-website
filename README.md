# ec2-website

# 1-create ec2 keypair
        dev-key
# 2-create security group
        ec2_security_group
        allow shh,http

# 3-create an EC2 and AMI
        custom_webser_ami
        description: webserver starter ami
        
# 4-craete a launch template
        custom_webserver_template
        intsance type
        key-pair
        security group
        instance profile
        metadata version v1,v2
        
# 5-deploy an autoscaling group
        webserver_asg
        launch template
        vpc
        public subnets
        2,1,2
        Name: webserver
        
        
# 6-aws ystem manager run command
        AWS-RunShellScript
        
        #!/bin/bash
        yum -y update
        yum -y install httpd php
        chkconfig httpd on
        wget https://github.com/bestdevopsengineer/ec2-website/raw/main/phpapp.zip
        unzip phpapp.zip -d /var/www/html/
        service httpd start

# 7- create load balancer

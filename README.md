# VPC-Task

The purpose of this task is to:

1. Set up two instances in a private network in  AWS and deploy an Ngix webserver on both.

2. Create an ALB to route requests to these instances and ensure they display their hostname or IP adress. 

The first step in this task is to ensure that
an AWS account has been created. log in to account and choose a preferred region.

search for VPC in the services section.

# Create VPC
choose the VPC and others option , so that it automatically creates the subnets, route tables for you.

![screenshot of vpc](/IMAGES/create%20vpc.png)
Click on nat gateway, so that it creates one nat gateway to give internet access to your private instances.


![screenshot of nat gateway](/IMAGES/nat%20gateway%20and%20create%20vpc.png)Two subnets each are created for private and public. Preview the subnets and route-tables and click on create VPC.


1[screenshot of created VPC](/IMAGES/showing%20vpc%20created.png)


# Create EC2 Instances
You would need to create two private instances and one bastion host.

click on launch instance.


![screenshot of laucnch instance option](/IMAGES/)

Create a name for you instance.


![sc of instance name](/IMAGES/)


Choose your preferred linux distro. For the purpose of this course, we would use Ubuntu.

Choose a key pair

![sc of ubuntu linux](/IMAGES/ubuntu%20instance.png)


Click on edit network configurations.


1. Choose the newly created VPC as the option for your instance to be placed in.

2. Place it in one of the private subnets.

3. Disable the automatic creation of a public IP adress 
4. Create a security group and click launch instance. Repeat same for the second instance. 

![sc of edited network settings](/IMAGES/edit%20network%20settings.png)

# Create Bastion Host

A bastion host is a server with which you can access your private instances.
1. Create a name for your bastion host.

2. select a key pair

3. place the instance in the newly created VPC and in the public subnet this time around. Enable public IP and choose existing security group. 
4. click on launch instance. 
5. Now ssh into your bastion host with your key pair.
6. chmod 400 the selected key pair and ssh with the ip into your bastion host
7. The bastion host would now be used to log-in to your private instances. 
8. copy key pair  into your bastion host chmod 400 the copied key and use it to ssh into instance. 
9. sudo apt update 
10. sudo apt update; sudo apt install nginx -y; sudo su to log into the root user and install ngix server.

11. Use the command echo "<h1>This is my server $(hostname -f)</h1>" > /var/www/html/index.nginx-debian.htmlecho to displa our servername

12. Use the cat to confirm that it was successful  
* cat /var/www/html/index.nginx-debian.html
do the same for second instance. 

# Create target group
choose your target group name.

![sc of target group creation](/IMAGES/click%20on%20target%20groups.png)
![sc of target group creation](/IMAGES/target%20group%20vpc.png)
![sc](/IMAGES/target%20group%20vpc.png)
![sc](/IMAGES/target%20group%20configuration.png)


# Create Load Balancer

![sc](/IMAGES/choose%20lb%20name.png)
![sc](/IMAGES/configure%20security%20group%20lb.png)
![sc lb group creation](/IMAGES/lb%20url.png)
Create security group for load balancer.


# Check to see if target group is healthy.

![sc of healthy target groups](/IMAGES/check%20if%20healthy.png)

# Use Load balancer DNS to see if IP Adress displayed successfully. 

![server1 image](/IMAGES/server1.png)
![server 2 image](/IMAGES/server2.png)




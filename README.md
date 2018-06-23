# Raghiu
Congnitive
Openresty
Congnitive

Creation of AWS Account
created the AWS account and created the IAM user. Created a new policy with Ec2 full access and Cloud formation access. Downlaod the credentials files as well.

###################################################################

Lauching a new Instance
As per the document i've used AWS CLI tools to launch the VM using AWS Cloud Formatoin template. As there were no specific requirenment i've use Centos7.5 Image becuase I've been using it from last couple of years and more over Redhat is costly when compared with Oracle and Centos. OS : Centos7.5 InstanceType : As i need to use only free Tier instance so I've used t2.micro, reason : AWS offers free Tier only for t2.micro instance. Security Group: As it was requested in the use case to allow access to only from specified office netwrok but didn't provided the public IP of the office locaitons so i've used my current locaiton public IP and provided the access to follwoing ports only as this is webserver i've launched the server in public subnet. As this is in Public subnet attached the EIP to access the same from putty and browser aswell. Inbout rules : 22,80,443 for my ISP.

for executing the template.

aws cloudformation create-stack --stack-name Openresty-stack --template-body file:///root/Openresty/Openresty.yml

##########################################################################################################################################

###installing the “Openresty” webserver on the VM using configuration management tool. Configruation Managment tool : Ansible. (Reason : I've been using this and bit easy to write a yml scirpt when compared with other configuration management tools.

prerequisite: used Password less authentication between the VM's.
Both of my VM's are running under same account i've goahed and used password less authentiction method to proceed with and alogn with allowing the inbound rule to have access from Ansible Server.

created a simple play book which will download the source code from github as per the requirenment and execute the build scirpt. what exactly the scirpt will be doing here is dowload the repository on the remote VM and execute the script

when i was executing the build script i was facing some issues and build was not executing as per the request, so i've modified it slightly and then executed it and after that it was working.

######################################################################################################################################

################################################################################################################################
Monitoring Part: 

Not sure exactly if you're asking me to install it or give some suggestion to monitor the application. 

so here are my suggestions we can go with Nagios core becuase this Opensource and widely used by every one in the market, monitoring tool for this and start monitoring the service based on the port number so that if at all the service is not started the port number will not be in use.  Once we have Nagios Core is setup we need to use nrpe agent which sould be installed on the remote VM to enable monitoring on the VM. 

Note: If we're going with default installation of Nagios Core then we need to update the contacts.cfg file under this lacation : /usr/local/nagios/etc/objects

then under hosts directory we need to update the services.cfg 

#####################################################################################################################################



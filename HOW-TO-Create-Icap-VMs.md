## Creating ICAP-Servers on AWS

Get Latest AMI for icap-server from here : https://github.com/k8-proxy/GW-Releases/actions?query=workflow%3Aicap-server

Deploy multiple instances from the selected AMI :
* Open aws console, on ec2. Click on AMI, search the ami which you got on the first step and click on launch
* Instance count : The amount of requested instances
* Instance type : For load testing we generally use c4.8xlarge but ask to requester which flavour he wants to use
* Disk space : At least 50G
* Security 
* Private key : packer.pem

Record the created instances IP addresses and provide them to Nader for configuring load balancer.

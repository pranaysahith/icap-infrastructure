# Creating ICAP-Servers on AWS

Follow the below steps to deploy icap-server in AWS.

- Login to aws console https://aws.amazon.com/console/
- Go to EC2 service
- Choose "eu-west-1" region
- Choose "AMI" under "Images" from left Sidebar under 
- Click twice on "Creation Date" column to get latest AMIs
- Select latest AMI with name "icap-server"
- Click on "Launch" button

    ![image](https://user-images.githubusercontent.com/64204445/105376034-525d5a00-5c2f-11eb-9971-94350e4b3793.png)
  
- Select below configarature for next steps:
        
        - Instance type     :     c4.8xlarge ( For load testing we generally use c4.8xlarge but ask to requester which flavour he wants to use ) 
        - Instance count    :     The amount of requested instances 
        - Disk space        :     At least 50G
        - Security Groups   :     Inbound rules: 22, 80, 443, 1344, 1345, 5601, 9100, 31829
                                  Outbound rules: All traffic
        - Private key       :     Choose existing or create a new pem file.
                           
    ![image](https://user-images.githubusercontent.com/64204445/105377964-57bba400-5c31-11eb-8c92-b80d419a8e82.png)        
        
    ![image](https://user-images.githubusercontent.com/64204445/105377004-5a69c980-5c30-11eb-90d7-97a60b6a95ff.png)
    
- Click "Launch" button and wait till the instance goes to running state

- Get the Public IP of the instance

- To test the icap-server, use below command and verify output should be similar to below screenshot.
  ( c-icap should be installed before this step )

       curl https://owasp.org/www-pdf-archive//01_18_10_OWASP_Newsletter.pdf --output sample.pdf
       /usr/bin/c-icap-client -i <IP> -p 1345 -tls -tls-no-verify -s gw_rebuild -f sample.pdf -o rebuilt.pdf -v
       
    ![image](https://user-images.githubusercontent.com/64204445/105380046-7c188000-5c33-11eb-883d-7e371ba111b6.png)


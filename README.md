![image](https://github.com/user-attachments/assets/06f579e3-3d5c-4269-b962-7a323c1acb15)# Complete Cloud Infrastructure with Generative AI
This repository is from AWS Solutions Architect CloudQuest. This solution demonstrates the speed up adoption of Infrastructure as Code (IaC) to deploy applications and infrastructure in a repeatable manner.

This is the diagram of this lab: 

![image](https://github.com/user-attachments/assets/2ca713bb-9d38-492d-9ce3-d5f6f5635422)
<sup>Author: SkillBuilder AWS</sup>

The app that is going to be deployed in this lab is a census application that displays the population values from different years and countries ***created by AWS***.
> [!NOTE]
> [Important CDK Concepts](Important-CDK-Concepts.md)

To have in mind ***both AWS CDK and CodeWhisperer are integrated directly to AWS Cloud9***

💡 In this lab, when CDK is written, CodeWhisperer will provide suggestions based on comments and the context of the existing code.

Finally, when the code is ***completed*** and ***tested***, it synthesized into a AWS CloudFormation template, which ***deploys*** the resources and applications that were defined in the CDK code.

> [!TIP]
> Build the template in the next order:

1. In the Cloud9 environment, create a folder for the CDK App named cdkapp = mkdir cdkapp
   
3. Enter the folder cdkapp = cd cdkapp
   
5. Initialize the cdk process running = cdk init -a app -l=python

   Review of each part of the command:

   - The "cdk init" command uses the name of the project folder to name various elements of the project, including classes, subfolders, and files. 
   - Using the "-a" option, you can specify an app name.
   - Using the "-l" option, you can specify the programming language
   
7. Create a virtual environment using = python3.8 -m venv .venv (in case you want to delete the venv created use = rm -rf .venv)
   
8. Activate the venv created using = source .venv/bin/activate
   
9. Create a txt file for the libraries required (aws-cdk library). Which are the mentioned below:
   
    aws-cdk-lib=2.137.0
    constructs>=10.0.0,<11.0.0
   
10. Install the requirements.txt created using = pip3.8 install -r requirements.txt
    
11. Put the userdata.sh file attached to the lab folder inside the Cloud9 cdkapp folder

      ![image](https://github.com/user-attachments/assets/64248511-6a3f-4789-bfcf-501e4cf9ee83)

   
   Short review of the userdata.sh file contents:

   - This file contains the libraries to be downloaded for the census application to run on an Amazon Elastic Compute Cloud (Amazon EC2) instance.
   - The vpcapp is the census application that displays the population values from different years and countries.
   - The database_populate function connects to the Amazon RDS database (DB) cluster and creates a population table with the data.
   - The application function starts the application

7. Go to the file cdk.json = cd cdkapp/tests/cdk.json
8. Change the "true" value to "false"

    ![image](https://github.com/user-attachments/assets/7315ca8d-874f-4b88-b96f-91201a19420d)
    <sup>Author: SkillBuilder AWS</sup>
    
9. Open the cdkapp_stack.py, initially it should appear something like this:
    
    ![image](https://github.com/user-attachments/assets/ccbcc53c-dc84-4c9b-802f-5b940a5a3f8e)

    Change the content inside the () to:

    ![image](https://github.com/user-attachments/assets/d2011fe1-3ae6-48bb-a256-02b55af0f464)

10. Delete this part of the code

    ![image](https://github.com/user-attachments/assets/f924c23c-0a6d-424f-8164-e8d8d7b5395c)

11. In the cdk.json (cdkapp/tests/cdk.json)

    - Create a virtual private cloud (VPC), in the top cdkapp_stack.py window, type:
      
           # create a vpc with IpAddresses 10.10.0.0/16, a NAT gateway, a public subnet, PRIVATE_WITH_EGRESS subnet and a RDS subnet

      ![image](https://github.com/user-attachments/assets/127dc450-6448-4f6c-882b-84bf38b556a2)

    - To create a security group for the load balancer, type:

            # create a security group for the load balancer
      
      ![image](https://github.com/user-attachments/assets/06c7fe04-1ce4-4180-b43a-cbf152991953)

    - To create a security group for the RDS instance, type:
      
            # create a security group for the RDS instance
      
    - To create a security group for the EC2 instance, type:

            # create a security group for the EC2 instance
      
    - To add inbound rules to the load balancer, type:

            # add ingress rules for the load balancer to allow all traffic
      
      ![image](https://github.com/user-attachments/assets/5626d76e-2369-4b52-bcb1-8ccd097f292f)

    - To allow traffic from the load balancer to the EC2 instance, type:

            # add ingress rule for the EC2 instance to allow 8443 traffic from the load balancer
      
    - To allow traffic for the RDS DB instance from the EC2 instance on port 3306, type:

            # add ingress rule for the RDS instance to allow 3306 from the EC2 instance
      
    - To allow traffic for the RDS DB instance from the EC2 instance on port 22, type:

            # add ingress rule for the RDS instance to allow 22 from the EC2 instance
      
    - To create an Amazon Aurora MySQL-Compatible Edition cluster, type:

            # create an rds aurora mysql cluster
   
      ![image](https://github.com/user-attachments/assets/dae555e0-bc77-4732-8bea-2910cfcc2466)
   
    - On the next line, to use predefined credentials, type:

            # credentials using testuser and password1234!
   
      ![image](https://github.com/user-attachments/assets/11a776a5-3185-4473-80a5-e5e0d7be8cb4)

    - Press Enter, and then, to get suggestions for the default database name, type:

            # add default database name Population
      
      ![image](https://github.com/user-attachments/assets/0dcfdf50-0e59-4056-9040-b45ebfa78497)

    - For instance_props, type:
      
            instance_props={
      At the end of the instance_props statement, press Enter and type:

            # add a vpc to the rds instance
      
      ![image](https://github.com/user-attachments/assets/9c0cb0fd-e543-4383-95b2-99939136a0e7)

    - To add a security group to the RDS instance, type:

            # add a security group to the rds instance
      
    - To add a private subnet to the RDS DB instance, type:

            # add a private subnet to the rds instance
      
    - Press Enter, and then, based on the CodeWhisperer suggestion, choose to close instance_props and add instances=1 to the RDS DB cluster.

         - Be sure to add only one instance to the cluster definition.
         - Be sure to close the cluster definition.

    Should look like this:

      ![image](https://github.com/user-attachments/assets/c503880b-af62-4540-8828-8ea249e77eaf)
      ![image](https://github.com/user-attachments/assets/3c203ec5-a579-444a-9247-335a7efd86ac)

    - To create an Amazon Linux 2 Image, type:

            # create an Amazon Linux 2 image
      
      ![image](https://github.com/user-attachments/assets/c2cc65b5-80ac-4c88-87c5-4fcd2f49e7ba)

    - To read the userdata.sh file, type:

            # read userdata file from cdkapp directory

      ![image](https://github.com/user-attachments/assets/8aed3875-abfe-4f05-9c11-40c395dd0265)

    - To create an EC2 instance for the web server in a private egress subnet, type:

            # create a t2.small ec2 instance for the web server in a private egress subnet and vpc.availability_zones[0]
      
      ![image](https://github.com/user-attachments/assets/f9a983d8-bb7b-4e33-9564-4dc430428d55)


    - To add an existing role with the name, ec2_instance_role, type:

            # add an existing role with name ec2_instance_role
      
      ![image](https://github.com/user-attachments/assets/0e18775c-1bae-48a2-9e62-7905dc98f406)

    - To create a load balancer, type:

            # create a load balancer for the web server

    - To create a listener for the load balancer, type:

            # create a listener for the load balancer

      ![image](https://github.com/user-attachments/assets/8de1c0ac-899d-4a32-8b4b-7edc21d53f72)

    - To add targets to the load balancer, type:

            # add targets to the load balancer
      
      - Be sure to add port=80 to the construct.
      - If you see a targets=[ec2_instance] field, remove it from the listener.add_targets
        
        ![image](https://github.com/user-attachments/assets/ad9db090-6c38-4146-8a3a-25cd974c880c)
        
    - To deploy the web server after the the RDS DB cluster is available, type:

            # add depends on for the web server to wait for the RDS cluster
      
    - To deploy the listener after the web server is up and running, type:

            # add depends on for the listener to wait for the web server
      
        ![image](https://github.com/user-attachments/assets/9c8c3c91-e21e-4bd9-9cf4-b428e475fb7e)

    - 1. On the top navigation bar, click File to expand the dropdown menu.
      2. Choose Save

    The bootstrap process has been run as part of the lab prebuild
    
> [!NOTE]  
> Bootstrapping is the process of provisioning resources for the AWS CDK before you can deploy AWS CDK apps into AWS environment

- To synthesize the CDK stack, in the bottom terminal window, run:

         cdk synth
  - 1. Review the stack details.
    2. To deploy the cdkapp stack, run:

           cdk deploy
   
    3. Type ***y*** after reviewing
       
       ![image](https://github.com/user-attachments/assets/b5f202fe-f81e-4f82-b0ff-fd3f67323781)

  - Review the stack components that are being deployed by the cdk process.

 > [!NOTE]
 > The deployment takes up to 15 minutes to be completed

   - In the other browser tab, navigate to the AWS CloudFormation console.
   - In the Stacks section, under Status, review to ensure that the status for the stack, CdkappStack, is CREATE_COMPLETE.
   - Click CdkappStack.
   
   - Follow the next images:

        ![image](https://github.com/user-attachments/assets/6dea0d27-c7b8-4780-bd93-6e9b3364d317)
        ![image](https://github.com/user-attachments/assets/0bb4efc7-7850-4653-b77f-b580c8e41839)
        ![image](https://github.com/user-attachments/assets/f0e00015-8813-420f-9fbb-badb2090c66b)
        ![image](https://github.com/user-attachments/assets/c1207838-d289-4e2e-a9eb-b32bcc2b2df1)
        ![image](https://github.com/user-attachments/assets/d8ec5dfc-a07a-4e12-babd-958c8aa20aa2)
        ![image](https://github.com/user-attachments/assets/bd481899-65a2-475f-9870-70f35d96e558)
        ![image](https://github.com/user-attachments/assets/531f8322-7e9c-4bb9-bb87-2832f4f53166)
        ![image](https://github.com/user-attachments/assets/bbfedc42-7d75-434e-89ef-738f0cd27ac1)
        ![image](https://github.com/user-attachments/assets/dff1ef2f-6e69-4798-b643-db8a05ac7b19)

   - Under Load balancer, click the provided load balancer name, open the Load Balancer link.

        ![image](https://github.com/user-attachments/assets/54a63364-c8dd-49ba-b0f0-cb47bfa05fdf)

   - Under DNS name, click the copy icon to copy the load balancer URL.
     
        ![image](https://github.com/user-attachments/assets/345e7f49-fb2c-467d-8215-c7363353a017)

   - After seeing the status of the load balancer as Active, follow the next final steps!
     
   1. To access the census application, in a new browser tab (or window) address bar, paste the load balancer URL that you just copied (not shown).

   2. You should see the Population Facts page with year and country options.

   3. Review the Availability Zone in which the instance is deployed.

         ![image](https://github.com/user-attachments/assets/ab7d9da9-dbf5-458d-8032-4c355a2d1f09)














      



    


    

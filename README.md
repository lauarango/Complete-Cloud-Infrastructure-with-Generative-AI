# Complete Cloud Infrastructure with Generative AI
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
    - 


    


    

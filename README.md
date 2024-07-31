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

1. In the Cloud9 environment, create a folder for the CDK App.
   
3. Create a virtual environment using = python3.8 -m venv .venv (in case you want to delete the venv created use = rm -rf .venv)
   
5. Activate the venv created using = source .venv/bin/activate
   
7. Create a txt file for the libraries required (aws-cdk library). Which are the mentioned below:
   
    aws-cdk-lib=2.137.0
    constructs>=10.0.0,<11.0.0
   
9. Install the requirements.txt created using = pip3.8 install -r requirements.txt
    
11. Put the userdata.sh file attached to the lab folder inside the Cloud9 cdkapp folder

    Short review of the userdata.sh file contents:

 - This file contains the libraries to be downloaded for the census application to run on an Amazon Elastic Compute Cloud (Amazon EC2) instance.
 - The vpcapp is the census application that displays the population values from different years and countries.
 - The database_populate function connects to the Amazon RDS database (DB) cluster and creates a population table with the data.
 - The application function starts the application

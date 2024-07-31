### Important Concepts (CDK and CloudFormation)

![image](https://github.com/user-attachments/assets/f592e769-945a-4ae0-8f01-0753f3aed8cd)
<sup> by AWS SkillBuilder </sup>

## AWS CloudFormation
AWS CloudFormation is a service provided by Amazon Web Services (AWS) that allows you to model, provision, and manage AWS and third-party resources by treating infrastructure as code. With CloudFormation, you can describe the desired state of your infrastructure using templates written in JSON or YAML.

#### Key Concepts of AWS CloudFormation:

- Template: A JSON or YAML file that describes the resources and their configurations.

- Stack: A collection of AWS resources that are created and managed as a single unit. When you create a stack, CloudFormation provisions the resources defined in the template.
  
- Change Sets: A summary of the proposed changes CloudFormation will apply to a stack. It allows you to preview changes before applying them.
  
- Drift Detection: A feature that detects changes to stack resources outside of CloudFormation.

- Libraries: Pre-packaged modules for common use cases, providing reusable, higher-level constructs.

## AWS CDK (Cloud Development Kit)
The AWS Cloud Development Kit (CDK) is an open-source software development framework to define your cloud application resources using familiar programming languages. It allows you to write infrastructure as code using high-level, object-oriented languages like TypeScript, JavaScript, Python, Java, and C#.
  
#### Construct

Construct is a fundamental concept in the AWS CDK. Constructs represent AWS resources, or higher-level abstractions built using multiple resources.

Types of Constructs:

- Level 1 (L1) Constructs: Low-level constructs that directly correspond to AWS CloudFormation resources.

- Level 2 (L2) Constructs: High-level constructs that provide a more abstract and easier-to-use interface. They often encapsulate multiple L1 constructs.

- Level 3 (L3) Constructs: Even higher-level abstractions that often encapsulate multiple L2 constructs, representing complex infrastructure patterns.

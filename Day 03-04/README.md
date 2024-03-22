# AWS COMPUTE
Day(s) Tasks: **Understand the types, pricing, and use cases of EC2 instances**


AWS compute is powered by a powerful resource(s) called EC2 (Elastic Cloud Compute).
An EC2 instance is simply a virtual server

## EC2 Instances types
AWS provides a diverse range of EC2 instances to choose from tailored for specific use cases and optimized to deliver precise performance. These instances adhere to a naming convention that includes 3 key elements:
- **Instance class (e.g, m )**: Represents the general instance family.
- **Generation (e.g, 3)** : Denotes the iteration or generation of the instance type
- **Size (e.g., xlarge)** : Specifies the specific size or capacity within the instance class.

The table below summarizes the instance types, its characteristics and the examples in each category.

|Instance type      |Characteristics                           |Exaples         |
|:------------------|:---------------------------              |:---------------|
|1. General purpose instances|- Great for the diversity of workloads such as web servers|
|                             |- The configuration is well balanced between Compute, Memory, and Networking| T2, T3a, T3, T4g, M4, M5a, M5zn, M5n, M5, M6a, M6in, M6i, M6g, Mac, M7a, M7i-flex, M7i, M7g|
|2. Compute optimized instances|- Great for compute intensive tasks that require high-performance processor
|                                |- Use cases: Batch processing, Media Transcoding, High Performance Computing, Dedicated Gaming Servers| C4, C5a, C5n, C5, C6a, C6in, C6i, C6gn, C6g, C7a, C7i, C7gn, C7g|
|3. Memory optimized instances| - This instance is suitable for workloads which fast performance to process large datasets.| 
|4. Storage optimized instances| - Great for storage instensive tasks that require high, sequential read and write to large data set in local storage|H1, D3en, D3, D2, I3en, I3, I4i, Is4gen, Im4gn |
|5. Accelerated computing| - are the latest generation of GPU-based instances and provide the highest performance in Amazon EC2 for deep learning and high performance computing (HPC).|VT1, F1, DL2q, DL1, Inf1, Inf2, Trn1, G3, G4ad, G4dn, G5, G5g, P2, P3, P4|

## EC2 Pricing
The table below summarizes the EC2 pricing options:

|Pricing option|Characteristics|
|:-------------|:---------------|
|1. On-Demand instances|-Pay for what you use|
| |-Has the highest cost, No upfront payment|
| |-No long term commitment|
| |-Recommended for short term and un-interrupted workloads, where you can’t predict how application will behave|
|2. Savings plan|-Reduce your Amazon EC2 costs by making a commitment to a consistent amount of usage, in USD per hour, for a term of 1 or 3 years|
||-Recommended for steady state usage application (Database)|
|3. Reserved instances|-Reduce your Amazon EC2 costs by making a commitment to a consistent instance configuration, including instance type and Region, for a term of 1 or 3 years.|
|4. Spot instances|-Purchase unused instance capacity|
||-Upto 90% off compared to on-demand pricing|
||-Prices controlled by AWS based on supply and demand|
||-2 minutes notice prior to termination|


## Launch an instance on the management console
The procedure for launching an instance on the AWS management console is straight forward and has been well explained in this [article](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/option3-task1-launch-ec2-instance.html)

## Launch an EC2 instance using Terraform
This is me being that "extra" kind of student. I recently discovered and learnt how fun and easy it is to launch an EC2 instance on terraform.
The code snippets below shows the process followed to create an EC2 instance:

### ec2_main.tf file
This file specifies the provider, in this case **AWS**, the resurce I am creating (**EC2 instance**) and give any other specifications related to the instance i am launching. I leveraged the use of variables to provide flexibility in the code and reusability. It is also good security practice to avoid hard-coding your access and security keys.

```
provider "aws" {
    access_key = var.access_key
    secret_key = var.secret_key
    region = "us-east-1"
    
}

resource "aws_instance" "terraform_instance" {
    ami = var.ami
    instance_type = var.instance_type
    subnet_id = var.subnet_id
    

    tags = {
        Name = "HelloInstance"
    }
  
}
```

### ec2_variables.tf
This is where I have set up the necessary variables. These variables let me pass in values, and ensure the code is repeatable.
I set up the **ec2_variables.tf** file to include these variables:
- The **Amazon Machine Image(AMI)** id
- The **instance type** with the default being **t2.micro**
- The **subnet_id** with its default

```
variable "access_key" {
    description = "Access key to the console"
  
}
variable "secret_key" {
    description = "Secret key to the console"
  
}

variable "ami" {
    type = string
    default = "ami-0c101f26f147fa7fd"
  
}
variable "instance_type" {
    type = string
    default = "t2.micro"
  
}
variable "subnet_id" {
    description = "The VPC subnet the instance(s) will be created in"
    default = "subnet-0a18161a085298b3a"
  
}
```
### Execution
To launch your instance, run the code `terraform init` to initialize terraform.
![image](https://github.com/achenchi7/AWS-Projects-2023-2024/blob/main/images/terraform%20init.png))

Next run `terraform plan`

![image2](https://github.com/achenchi7/AWS-Projects-2023-2024/blob/main/images/terraform_plan.png)


Finally, run `terraform apply`. If successful you should get a green light as shown below

![image](


# Task(s): Launch an EC2 instance with the free tier.

## Launch an instance on the management console
The procedure for launching an instance on the AWS management console is straightforward and has been well explained in this [article](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/option3-task1-launch-ec2-instance.html)

## Launch an EC2 instance using Terraform

#### Specification:
Region - US-east -1
Availability zone - A random one will be selected by AWS within us-east-1. To specify an availability zone, add the preferred availability zone in the 'provider' section. (see the commented line)

This is me being that "extra" kind of student. I recently discovered and learned how fun and easy it is to launch an EC2 instance on Terraform.
The code snippets below show the process followed to create an EC2 instance:

### ec2_main.tf file
This file specifies the provider, in this case, **AWS**, the resource I am creating (**EC2 instance**) and gives any other specifications related to the instance I am launching. I leveraged the use of variables to provide flexibility in the code and reusability. It is also good security practice to avoid hard-coding your access and security keys.

```
provider "aws" {
    access_key = var.access_key
    secret_key = var.secret_key
    region = "us-east-1"
    # availability zone = "us-east-1a"
    
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
This is where I have set up the necessary variables. These variables let me pass in values and ensure the code is repeatable.
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

![image](https://github.com/achenchi7/AWS-Projects-2023-2024/blob/main/images/terraform_apply.png)

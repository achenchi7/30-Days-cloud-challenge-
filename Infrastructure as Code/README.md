# What is Infrastructure as Code?
Infrastructure as Code, commonly known as IaC is the process of **codifying** the provisioning of cloud resources. Instead of using a cloud-specific management console, a code is written to deploy resources in the cloud.

### Benefits of Utilizing IaC
- It is a fast process
- Several resources can be deployed in one single script
- Monitoring of resources is easier
- Code reusability

## Types of IaC tools
IaC tools can be classified into 3 classes:
- Configuration management tools - Tools here are **Ansible**, **Puppet**, and **SaltStack**
- Server templating tools - Tools here are **Docker**, **Packer**, and **Vagrant**
- Provisioning tools - **Terraform**, and **CloudFormation**

# TERRAFORM
Terraform is an IaC tool used for provisioning cloud resources in the cloud.\
It was developed by HashiCorp and used the HashiCorp Configuration Language (HCL) as its syntax.\

### HCL syntax
```
resource "local_file""pets"{
       filename = "/root/user/pets.txt"
       content = "I love pets"
}
```
**resource** is the bloc of code\
**local** is the provider name. Terraform supports over 100 [providers](https://registry.terraform.io/browse/providers) of which **local** is one of them\
**file** is the specific resource you want. In this case, file is the resource\
**filename and content** are arguments in key-value format\

HCL is a simple declarative language to define the infrastructure resources to be provisioned as blocks of code.\
- **Declarative state** - The code is defined in a state that we want our infrastructure to be in. Terraform will take care of what is required to move from the current state to the desired state.

To do this, terraform works in three stages:
1. **`Terraform init`**\
In this phase, Terraform initializes the project and identifies the providers to be used for the target environment

2. **`Terraform plan`**\
Terraform drafts a plan to get to the desired state

3. **`Terraform apply`**\
Terraform makes the necessary changes required in the environment to move it from the current state to the desired state.

### Terraform state
Terraform state file `terraform.tfstate` is a file that is created when you run `terraform apply` at least once.\
It is a JSON data structure that maps the real-world infrastructure resources to the resource definition in the config files.

## Additional terraform commands
1. `terraform validate` - Used to check if your syntax is correct.\
2. `terraform fmt` - This command scans the config files in the current working directory and formats the code into a canonical format. It is useful to improve the readability of your configuration file.\
3. `terraform show` - It prints out the current state of your infrastructure as seen by terraform.\
4. `terraform providers` - Prints out all the providers used in your configuration files.\
5. `terraform output` - Prints out all the output variables in your config files.\
6. `terraform output <variable-name>` - Prints out the specific output of the variable defined.\
7. `terraform refresh` - Used to sync terraform with the real-world infrastructure. This command will only modify the state file and not the infrastructure.\
8. `terraform graph` - Used to create a visual representation of the dependencies and a terraform configuration or an execution plan. The output of this command is a file with the format **dot**. To make it make sense, you can visualize this through an application like **graphviz**

## Version constraints
This is applied if you desire to use a specific version of your required provider. By default, running `terraform init` downloads the latest version of your specified provider.\

In cases where you want to use a specific provider, here is the syntax:\
NB: The latest version of the provider **local** is 2.5.1. The code below will install version 2.5.0
```
terraform {
  required_providers {
    local = {
      source = "hashicorp/local"
      version = "2.5.0"
    }
  }
}
```

# Remote state and state Locking
As stated earlier, a terraform state file is created when terraform apply is run at least once in the configuration files. The benefits of the state file include:
- Mapping configuration to the real world
- Tracking metadata
- Improves performance especially when working with different providers.

The state file is stored and accessed in two ways:\
a. **Local state file** - This is created in your local machine and specifically in the config directory you are working in.\
          **Disadvantage** - Does not allow for collaboration within teams

b. **Remote backend** - The state file is stored and accessed from a shared storage such as Google Cloud, S3 bucket, or Terraform Cloud.\
          **Advantage**- It is secure and updates on the state file can easily be tracked

### State Locking
State locking is a built-in mechanism within a terraform state that prevents the state file from being updated simultaneously. If one individual is working on the state file, terraform automatically locks the file and prevents any further changes until the current changes have been implemented.

## Terraform state commands
The syntax is `terraform state [sub-command] [arguments]`
The various commands are:\
a. `terraform state list` - This will list all the resources recorded in the terraform state file\
b. `terraform state show` - This will show detailed information of a single reseorce\
c. `terraform state mv [options] SOURCE DESTINATION` - Used to move items in a tfstste file



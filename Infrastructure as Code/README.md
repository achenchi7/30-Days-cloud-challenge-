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
9. 


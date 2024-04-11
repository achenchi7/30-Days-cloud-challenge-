I chose to launch a MySQL database on AWS using terraform instead of the conventional management console. The code used is as shown below:
```
provider "aws" {
    access_key = <ACCESS_KEY>
    secret_key = <SECRET_KEY>
    region = "us-east-1"

    
  
}

resource "aws_db_instance" "terradb" {
    allocated_storage = 20 # Minimum storage allowed.
    engine = "mysql" # The engine my database will run on
    instance_class = "db.t3.micro" # A base instance type to remain within the free tier
    username = "<username>"
    password = "<password>"
    skip_final_snapshot = true

  
}
```
The attributes described here are briefed as follows.

- **allocated_storage:** Is the Memory allocated in GB for this database instance. The minimum allowed is 20Gb
- **engine:** Is the Choice of the database engine. I have selected MySQL as the desired database engine. Other options include Postgres, MariaDB, Oracle, etc.
- **instance_class:** Defines the dimensions of instance to provision based on various factors like CPU, memory, networking, and storage.
- **username:** The user name of the main database user (admin).
- **Password:** Password for the main database user (admin). This should be supplied in a secure way. 
- **skip_final_snapshot:** Determines if a snapshot should be taken before deleting the database. The database can be created without setting this setting. However, while destroying this database instance using Terraform, if this value is not set to true, the database is not destroyed.

To launch the db instance, run `terraform init` to initialize terraform,
![Terraform init](https://github.com/achenchi7/AWS-Projects-2023-2024/blob/main/images/terraform%20init.png)

Next, run `terraform plan` which creates an execution plan, which lets you preview the changes that Terraform plans to make to your infrastructure.

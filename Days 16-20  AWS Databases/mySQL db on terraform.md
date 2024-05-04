I chose to launch a MySQL database on AWS using Terraform instead of the conventional management console. The code used is as shown below:
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
![Terraform plan](https://github.com/achenchi7/AWS-Projects-2023-2024/blob/main/images/terraform%20plan_db.png)

Finally, run `terraform apply` to execute the changes laid out above. The process might take a few minutes depending on how complex your database is. Might be a good time to stretch your legs.

![terraform apply](https://github.com/achenchi7/AWS-Projects-2023-2024/blob/main/images/terraform%20apply1.png)

My database took 3m 30sec to be created

![time taken](https://github.com/achenchi7/AWS-Projects-2023-2024/blob/main/images/terraform%20apply_db2.png)

The beautiful green light that your process was successful
![green light](https://github.com/achenchi7/AWS-Projects-2023-2024/blob/main/images/terra%20apply_db3.png)

## Confirmation
To confirm further the creation of the database, navigate to your AWS management console and under RDS, you should see your database as I mine.

![db instance](https://github.com/achenchi7/AWS-Projects-2023-2024/blob/main/images/db%20instance%20on%20aws.png)



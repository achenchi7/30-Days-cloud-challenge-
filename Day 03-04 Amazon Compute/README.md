# AWS COMPUTE
Day(s) Tasks: **Understand the types, pricing, and use cases of EC2 instances**


AWS compute is powered by a powerful resource(s) called EC2 (Elastic Cloud Compute).
An EC2 instance is simply a virtual server

## EC2 Instances types
AWS provides a diverse range of EC2 instances to choose from tailored for specific use cases and optimized to deliver precise performance. These instances adhere to a naming convention that includes 3 key elements:
- **Instance class (e.g, m )**: Represents the general instance family.
- **Generation (e.g, 3)** : Denotes the iteration or generation of the instance type
- **Size (e.g., xlarge)**: Specifies the specific size or capacity within the instance class.

The table below summarizes the instance types, its characteristics, and the examples in each category.

|Instance type      |Characteristics                           |Exaples         |
|:------------------|:---------------------------              |:---------------|
|1. General purpose instances|- Great for the diversity of workloads such as web servers|
|                             |- The configuration is well balanced between Compute, Memory, and Networking| T2, T3a, T3, T4g, M4, M5a, M5zn, M5n, M5, M6a, M6in, M6i, M6g, Mac, M7a, M7i-flex, M7i, M7g|
|2. Compute-optimized instances|- Great for compute-intensive tasks that require high-performance processor
|                                |- Use cases: Batch processing, Media Transcoding, High-Performance Computing, Dedicated Gaming Servers| C4, C5a, C5n, C5, C6a, C6in, C6i, C6gn, C6g, C7a, C7i, C7gn, C7g|
|3. Memory-optimized instances| - This instance is suitable for workloads with fast performance to process large datasets.| 
|4. Storage optimized instances| - Great for storage-intensive tasks that require high, sequential read and write to large data sets in local storage|H1, D3en, D3, D2, I3en, I3, I4i, Is4gen, Im4gn |
|5. Accelerated computing| - is the latest generation of GPU-based instances and provides the highest performance in Amazon EC2 for deep learning and high-performance computing (HPC).|VT1, F1, DL2q, DL1, Inf1, Inf2, Trn1, G3, G4ad, G4dn, G5, G5g, P2, P3, P4|

## EC2 Pricing
The table below summarizes the EC2 pricing options:

|Pricing option|Characteristics|
|:-------------|:---------------|
|1. On-Demand instances|-Pay for what you use|
| |-Has the highest cost, No upfront payment|
| |-No long term commitment|
| |-Recommended for short-term and un-interrupted workloads, where you can’t predict how an application will behave|
|2. Savings plan|-Reduce your Amazon EC2 costs by making a commitment to a consistent amount of usage, in USD per hour, for a term of 1 or 3 years|
||-Recommended for steady-state usage application (Database)|
|3. Reserved instances|-Reduce your Amazon EC2 costs by making a commitment to a consistent instance configuration, including instance type and Region, for a term of 1 or 3 years.|
|4. Spot instances|-Purchase unused instance capacity|
||-Upto 90% off compared to on-demand pricing|
||-Prices controlled by AWS based on supply and demand|
||-2 minutes notice before termination|

## EC2 use cases
### 1. Run Cloud- native and enterprise applications
EC2 instances deliver secure, reliable, high-performance, and cost-effective computing infrastructure to meet demanding business needs

### 2. Train and deploy ML applications
EC2 delivers the broadest choice of computing, networking(up to 400Gbps), and storage services, purpose-built to optimize price performance for ML projects.


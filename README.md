# EC2 Launch Template & EBS Volume Performance Testing (Using AWS CLI + FIO)

> <!-- I created a Launch Template -->
## 1. Launch Template Creation
In this project, I created an EC2 *Launch Template* using the AWS CLI.  
The template defines the instance configuration such as AMI, instance type, key pair, security groups, and storage settings.  
This allowed me to launch EC2 instances quickly using the same predefined configuration.

---

> <!-- I launched an instance from the Launch Template -->
## 2. Launching an EC2 Instance
After preparing the Launch Template, I launched an EC2 instance *directly from the template* using the CLI.  
This ensured that the instance inherited all the predefined settings without manually configuring each option.

---

> <!-- I created an EBS volume -->
## 3. Creating an EBS Volume
Next, I created an additional *EBS volume* from the AWS CLI.  
The volume was created in the same availability zone as the EC2 instance to ensure compatibility.

---

> <!-- I attached the EBS volume to my instance -->
## 4. Attaching the Volume to the Instance
After creating the volume, I attached it to the EC2 instance (launched from the template).  
The volume was then visible under /dev/nvme* or /dev/xvd* depending on the instance family.

---

> <!-- I used FIO to test the performance -->
## 5. Performance Testing with FIO
I performed a full performance analysis using the *fio* benchmarking tool.  
The tests helped me evaluate:
- *IOPS (Input/Output Operations per Second)*
- *Throughput*
- *Latency*
- *Behavior under high I/O depth*

I tested different block sizes, queue depths, and random write patterns to observe how the volume performs under different workloads.

---

> <!-- I checked the results from both CLI and AWS Console -->
## 6. Reviewing Metrics
After running fio, I reviewed the performance metrics from:
- *FIO output logs in the CLI*  
- *AWS Console (CloudWatch metrics)* including:
  - Volume IOPS
  - Throughput
  - Burst credit usage
  - Latency graphs

This helped compare what fio sees from inside the instance versus what AWS monitors at the volume level.

---

## Summary
This repository documents the full workflow of:
1. Building a Launch Template  
2. Launching an EC2 instance  
3. Creating and attaching an EBS volume  
4. Running fio performance benchmarks  
5. Reviewing EC2/EBS performance metrics  

All steps were executed *entirely through the AWS CLI*.

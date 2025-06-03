<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Launch a Kubernetes Cluster

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-eks1)

**Author:** Vijay Pratap Singh Hada  
**Email:** vijaypratapsinghhada9@gmail.com

---

## Launch a Kubernetes Cluster

![Image](http://learn.nextwork.org/blissful_yellow_calm_donkey/uploads/aws-compute-eks1_e5f6g7h8)

---

## Introducing Today's Project!

In this project, I will deploy my first kubernetes cluster using Amazon EKS. This is because EKS is a AWS managed service that helps you run and scale containerized appplications without worrying about the underlying infrafstructure and I will also going to learn few more tools like eksctl and CloudFormation.

### What is Amazon EKS?

Amazon EKS (Elastic Kubernetes Service) is a managed service that helps deploy and manage Kubernetes clusters easily. In today's project, I used EKS to create a Kubernetes cluster for running containerized applications without worrying about the underlying infrastructure. This allowed me to focus on building and managing my applications efficiently.

### One thing I didn't expect

One thing I didn't expect in this project was the eksctl tool. I was surprised by how much it simplified the process of creating and managing EKS clusters. It made handling Kubernetes much easier than I anticipated, allowing me to focus on my applications instead of getting bogged down in configuration details.

### This project took me...

This project took me a total of 80 minutes: 50 minutes for hands-on learning and 30 minutes for documentation. The longest part was the hands-on learning, as setting up the EKS cluster and troubleshooting any issues required careful attention and understanding of the tools involved.



---

## What is Kubernetes?

Kubernetes is an open-source platform that helps automate the deployment, scaling, and management of applications packed in containers. It acts like a conductor, ensuring that all containers work together smoothly. Companies and developers use Kubernetes to simplify the challenges of running large applications. It automates tasks such as coordinating containers across different servers, adjusting resources as needed, restarting any containers that fail, and updating applications without causing downtime. 

I used eksctl to make it easier to create and manage Amazon EKS clusters. The create cluster command I ran set important details like the cluster name, Kubernetes version, and the types of EC2 instances for the worker nodes. It also defined how many nodes I wanted and specified the AWS region where the cluster would be built.

I initially ran into two errors while using eksctl. The first one was because I hadn't installed eksctl yet, which resulted in a message saying the command wasn't found. The second error happened because my EC2 instance didn't have permission to create an EKS cluster. I needed to set up an IAM role to allow my instance to communicate with AWS services. 

![Image](http://learn.nextwork.org/blissful_yellow_calm_donkey/uploads/aws-compute-eks1_ff9bfc221)

---

## eksctl and CloudFormation

CloudFormation helped create my EKS cluster because it automates the process of setting up all the necessary resources. When I ran the eksctl command, it used CloudFormation to create a stack that includes various components for my cluster. It created VPC resources because these components, like subnets and security groups, help establish a secure network for my containers.

There was also a second CloudFormation stack for the node group, which consists of EC2 instances that run my containers. The difference between a cluster and a node group is that the cluster represents the entire environment managed by Kubernetes, including both the control plane and the nodes. The nodes are the actual servers running the containers, and they are organized into node groups for easier management. This way, I can adjust settings, resources, and scale the nodes more effectively without having to change each one individually.

![Image](http://learn.nextwork.org/blissful_yellow_calm_donkey/uploads/aws-compute-eks1_w3e4r5t6)

---

## The EKS console

I had to create an IAM access entry in order to ensure that my AWS IAM user could access the nodes in my EKS cluster. An access entry connects my IAM user with Kubernetes' Role-Based Access Control (RBAC), allowing me to interact with the resources inside the cluster. I set it up by selecting my IAM user's ARN and applying the AmazonEKSClusterAdminPolicy, which grants full administrative rights over the cluster. 

It took 15 minutes to create my cluster. Since I’ll create this cluster again in the next project of this series, maybe this process could be sped up if I familiarize myself with the steps beforehand and ensure that all necessary permissions are correctly set up in advance.

![Image](http://learn.nextwork.org/blissful_yellow_calm_donkey/uploads/aws-compute-eks1_e5f6g7h8)

---

## EXTRA: Deleting nodes

Did you know you can find your EKS cluster's nodes in Amazon EC2? This is because each node in a Kubernetes cluster on AWS is actually an EC2 instance. Kubernetes uses the term “node” to describe the servers that run containers, but in AWS, these nodes are represented as EC2 instances. 

Desired size is the number of nodes you want running in your node group, which in this case is 3. Minimum and maximum sizes are helpful for ensuring your application remains available by maintaining at least the minimum number of nodes during low-demand periods, while allowing the maximum size to accommodate increased demand. 

When I deleted my EC2 instances, Kubernetes automatically detected the change and launched new instances to replace them. This is because Kubernetes is designed to maintain the desired state of the cluster, ensuring that the right number of nodes is always running to support my applications. This self-healing feature allows my apps to remain available, even if some nodes fail.

![Image](http://learn.nextwork.org/blissful_yellow_calm_donkey/uploads/aws-compute-eks1_q7r8s9t0)

---

---

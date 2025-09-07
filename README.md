# EKS ALB Ingress Demo

End-to-end EKS demo deploying a web app via AWS Load Balancer Controller (ALB) using a Kubernetes Ingress.

## Overview

This project demonstrates how to deploy a simple web application on Amazon EKS and expose it to the internet using the AWS Load Balancer Controller. The Ingress resource automatically provisions an Application Load Balancer (ALB) that routes HTTP traffic to your Kubernetes pods.

## Architecture

- **EKS Cluster**: Runs the application pods  
- **Deployment**: Manages multiple replicas of the web application  
- **Service**: Provides internal load balancing to pods  
- **Ingress**: Triggers ALB creation and configures routing rules  
- **ALB**: Routes external traffic to the service endpoints  

## Prerequisites

Before you begin, ensure you have:  
- An EKS cluster with worker nodes or Fargate profile  
- AWS Load Balancer Controller installed in the cluster  
- `kubectl` configured to access your EKS cluster  
- Proper IAM permissions for the Load Balancer Controller  
- Public subnets tagged for ALB discovery  


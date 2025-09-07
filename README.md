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
- kubectl – A command line tool for working with Kubernetes clusters. For more information, see Installing or updating kubectl.
- eksctl – A command line tool for working with EKS clusters that automates many individual tasks. For more information, see Installing or updating.
- AWS CLI – A command line tool for working with AWS services, including Amazon EKS. For more information, see Installing, updating, and uninstalling the AWS CLI in the AWS Command Line Interface User Guide. After installing the AWS CLI, we recommend that you also configure it. For more information, see Quick configuration with aws configure in the AWS Command Line Interface User Guide.


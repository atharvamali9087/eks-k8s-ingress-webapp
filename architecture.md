                        ┌────────────────────────────┐
                        │      AWS Account           │
                        │ (IAM Users, Roles, MFA)    │
                        └────────────┬───────────────┘
                                     │
                           ┌─────────▼─────────┐
                           │       VPC          │
                           │  (Public + Private │
                           │      Subnets)      │
                           └─────────┬─────────┘
                                     │
             ┌───────────────────────┼──────────────────────────┐
             │                       │                          │
 ┌───────────▼──────────┐  ┌─────────▼─────────┐      ┌─────────▼─────────┐
 │  Internet Gateway     │  │   Route Tables    │      │ Security Groups   │
 └───────────────────────┘  └──────────────────┘      └───────────────────┘
                                     │
                                     ▼
                            ┌─────────────────┐
                            │   EKS Cluster    │
                            │  (Control Plane) │
                            └─────────┬───────┘
                                      │
                           ┌──────────▼──────────┐
                           │ Worker Nodes (EC2)  │
                           │ (Private Subnets)   │
                           └──────────┬──────────┘
                                      │
                        ┌─────────────▼─────────────┐
                        │     Kubernetes Layer      │
                        │ ─ Namespace               │
                        │ ─ Deployment (NGINX Pods) │
                        │ ─ Service (ClusterIP)     │
                        │ ─ Ingress (ALB)           │
                        └─────────────┬─────────────┘
                                      │
                           ┌──────────▼───────────┐
                           │ Application Load      │
                           │ Balancer (Internet-   │
                           │ Facing via Ingress)   │
                           └──────────┬───────────┘
                                      │
                              ┌───────▼───────┐
                              │   End User    │
                              │ (Browser/API) │
                              └───────────────┘

1. Download IAM policy
   
         curl -L https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.11.0/docs/install/iam_policy.json -o iam_policy.json

2. Create IAM policy

         aws iam create-policy --policy-name AWSLoadBalancerControllerIAMPolicy --policy-document file://iam_policy.json

3. Create IAM Role

         eksctl create iamserviceaccount \
           --cluster CLUSTER-NAME \
           --namespace kube-system \
           --name aws-load-balancer-controller \
           --role-name AmazonEKSLoadBalancerControllerRole \
           --attach-policy-arn arn:aws:iam::YOUR_AWS_ACCOUNT_ID:policy/AWSLoadBalancerControllerIAMPolicy \
            --approve

5. Deploy via Helm

        helm repo add eks https://aws.github.io/eks-charts
        helm repo update
        helm install aws-load-balancer-controller eks/aws-load-balancer-controller \
          -n kube-system \
          --set clusterName=CLUSTER-NAME \
          --set serviceAccount.create=false \
          --set serviceAccount.name=aws-load-balancer-controller \
          --set region=REGION \
          --set vpcId=<your-vpc-id>

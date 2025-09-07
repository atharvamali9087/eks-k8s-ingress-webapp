kubectl apply -f https://raw.githubusercontent.com/atharvamali9087/eks-k8s-ingress-webapp/refs/heads/main/webapp.yaml

VERIFY DEPLOYMENT

    kubectl get pods -n web-namespace -w
    kubectl get all ingress -n web-namespace -o wide

Once the ADDRESS column shows your ALB DNS, open it in your browser to see the NGINX welcome page.

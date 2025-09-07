apiVersion: v1
kind: Namespace
metadata:
  name: web-namespace
---
apiVersion: apps/v1
kind: Deployment
metadata:
  namespace: web-namespace
  name: webapp-deployment
spec:
  replicas: 4
  selector:
    matchLabels:
      app: webapp
  template:
    metadata:
      labels:
        app: webapp
    spec:
      containers:
      - name: webapp
        image: nginx:1.25-alpine
        ports:
        - containerPort: 80
        resources:
          requests:
            cpu: "100m"
            memory: "128Mi"
          limits:
            cpu: "250m"
            memory: "256Mi"
---
apiVersion: v1
kind: Service
metadata:
  namespace: web-namespace
  name: webapp-service
spec:
  type: NodePort
  selector:
    app: webapp
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
---
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  namespace: web-namespace
  name: webapp-ingress
  annotations:
    alb.ingress.kubernetes.io/scheme: internet-facing
    alb.ingress.kubernetes.io/target-type: ip
spec:
  ingressClassName: alb
  rules:
    - http:
        paths:
        - path: /
          pathType: Prefix
          backend:
            service:
              name: webapp-service
              port:
                number: 80

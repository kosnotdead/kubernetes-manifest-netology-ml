# kubernetes-manifest-netology-ml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: netology-ml
spec:
  replicas: 2
  selector:
    matchLabels:
      app: netology-ml
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 1
      maxSurge: 1
  template:
    metadata:
      labels:
        app: netology-ml
    spec:
      containers:
      - name: tomcat
        image: tomcat:8.5.69
        ports:
        - containerPort: 8080

# Kubernetes Sample configuration

Sample instructions for a Microservice architecture with kubernetes.

This is a demo for a sample set of services:
- frontend (2 replicas)
- api (2 replicas)
- redis
- amq

We will use the following concepts:
- [ConfigMap](http://kubernetes.io/docs/user-guide/configmap/): Stores your environment variables
- [Services](http://kubernetes.io/docs/user-guide/services/): Describes your service network
- [Deployments](http://kubernetes.io/docs/user-guide/deployments/): Describes the Microservice deployments template.

## Initiate your Google Container Engine Cluster

```sh
# Set configuration information
gcloud config set compute/zone us-east1-b
gcloud config set project your-project-name

# Create GCE cluster
gcloud container clusters create my-cluster --num-nodes 2 --machine-type n1-standard-2 --zone us-east1-b

# Make sure you edited the project name in the yml files...

# Load ConfigMaps
kubectl create -f ./cm

# Load Services
kubectl create -f ./svc

# Load Deployments
kubectl create -f ./deploy

# Access to the dashboard
kubectl proxy > /dev/null &
# You'll be able to access to Kubernetes dashboard through:
# http://localhost:8001/api/v1/proxy/namespaces/kube-system/services/kubernetes-dashboard/#/workload
```

# Deploy your containers using a CI tool
Full instructions on: https://github.com/RefurbMe/k8s-deploy

## Contributions
Feel free to fork this project and open a PR with improvements!

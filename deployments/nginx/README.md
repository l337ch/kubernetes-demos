# Demoing the use of k8s Deployments

*Using examples from http://kubernetes.io/docs/user-guide/deployments/*

## Create a Deployments resource

Using the gke cluster created in the first README, create a nginx Deployment resource using `kubectl`
```
kubectl create -f deployments/nginx/nginx_deployments.yaml
```

# Demoing the use of k8s Deployments

*Using examples from http://kubernetes.io/docs/user-guide/deployments/*

## Create a Deployments resource

Using the gke cluster created in the first README, create a nginx Deployment resource using `kubectl`
```
kubectl create -f deployments/nginx/nginx_deployments.yaml --record
```
Check the nginx service
```
kubectl get service nginx --watch
```
Show some details of the newly create nginx Deployment
```
kubectl get deployments
kubectl get rs
kubectl get pods --show-labels
kubectl rollout status deployment/nginx-demo
```
Test the onnectivity to make sure nothing breaks during updates
```
while true; do curl -IsL 104.154.226.54 | grep "HTTP/1.1"; sleep 1; done;
```
Now update the nginx image to 1.9.1
```
kubectl set image deployment/nginx-deployment nginx=nginx:1.9.1
```

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
kubectl rollout status deployments nginx-demo
```
Test the onnectivity to make sure nothing breaks during updates
```
while true; do curl -IsL 104.154.226.54 | grep "HTTP/1.1"; sleep 1; done;
```
## Rollout and update

Now update the nginx image to 1.9.1
```
kubectl edit deployments nginx-demo
```
Edit the image to `image: nginx:1.9.1` and save and quit.

Check that the rollout was a success
```
kubectl rollout status deployment/nginx-demo
```

## Rollout a bad update
```
kubectl edit deployments nginx-demo
```
This time edit the image to `image: nginx:1.91` and save and quit.

Roll it back
```
kubectl rollout undo deployment/nginx-demo
```

## Clean up
Remove the nginx Deployment demo
```
kubectl delete deployment nginx-demo
```

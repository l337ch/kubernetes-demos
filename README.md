## Create a Google Container Engine Cluster

- Create a google container engine cluster with the gcloud commandline
```
gcloud container clusters create gke-zonar-demo  --zone us-central1-a \
--machine-type n1-standard-4 \
--num-nodes 3
```
- Gather credentials for kubeconfig to use with `kubectl`
```
gcloud container clusters get-credentials gke-zonar-demo
```
Proceed with demoing Deployments and Pet Sets

## Clean up
- Delete the google container demo cluster
```
gcloud container clusters delete gke-zonar-demo
```

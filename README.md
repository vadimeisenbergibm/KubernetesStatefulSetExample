# Kubernetes StatefulSet Example
An example of a Kubernetes stageful set

## Mounting persistent volumes on minikube

* `minikube mount www1:/tmp/www1 &`
* `minikube mount www2:/tmp/www2 &`

## Creating persistent volumes
* `kubectl apply -f www-volume1.yaml`
* `kubectl apply -f www-volume2.yaml`

## Deploying a StatefulSet
`kubectl apply -f statefulset.yaml`

## Deploy a sleep container for testing
`kubectl apply -f https://raw.githubusercontent.com/istio/istio/master/samples/sleep/sleep.yaml`

## Send Requests to the both nginx services
$ `kubectl exec -it $(kubectl get pods -o jsonpath='{.items[*].metadata.name}' -l app=sleep) -c sleep -- curl web-0.nginx`

Hello from Kubernetes storage 1

$ `kubectl exec -it $(kubectl get pods -o jsonpath='{.items[*].metadata.name}' -l app=sleep) -c sleep -- curl web-1.nginx`

Hello from Kubernetes storage 2

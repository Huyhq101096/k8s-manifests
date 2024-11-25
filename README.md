# k8s-manifests

    - create namespace for group k8s resources
        - namespace.yaml
        - reroursequota.yaml , # limit resources for namespace cpu, memory...

    step 1: create a pod
    step 2: create a service
    step 3: create a deployment

## create a pod
    - kubectl apply -f pod.yaml
    ## create a pod with new image
    - kubectl apply -f pod.yaml --image-pull-policy=Always

## create a service
    - kubectl apply -f service.yaml

## expose service
    - minikube service <name-service> -n <name-space> --url


## create replicaset
    - kubectl apply -f rs.yaml


## expose nodeport
    - kubectl expose replicaset.apps rs3 --name=
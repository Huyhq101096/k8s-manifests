# Install enviroment




# Create Cluster
    - sudo nano /etc/hosts
        * add:  127.0.0.1 control-plane-node (name control plan)
    - sudo kubeadm init --config=kubeadm-config.yaml

        To start using your cluster, you need to run the following as a regular user:

            mkdir -p $HOME/.kube
            sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
            sudo chown $(id -u):$(id -g) $HOME/.kube/config

            Alternatively, if you are the root user, you can run:

            export KUBECONFIG=/etc/kubernetes/admin.conf

            You should now deploy a pod network to the cluster.
            Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
            https://kubernetes.io/docs/concepts/cluster-administration/addons/

            You can now join any number of control-plane nodes by copying certificate authorities
            and service account keys on each node and then running the following as root:

            kubeadm join 10.1.2.40:6443 --token jr9uxs.s0ffz2fk0hwcciej \
                    --discovery-token-ca-cert-hash sha256:8db968977beb9205c369079e3787c876c3492bd12575ada1d482ecf3b65138c2 \
                    --control-plane 

            Then you can join any number of worker nodes by running the following on each as root:

            kubeadm join 10.1.2.40:6443 --token jr9uxs.s0ffz2fk0hwcciej \
                    --discovery-token-ca-cert-hash sha256:8db968977beb9205c369079e3787c876c3492bd12575ada1d482ecf3b65138c2 
    - mkdir -p $HOME/.kube
        sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
        sudo chown $(id -u):$(id -g) $HOME/.kube/config

    - kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml




# Check version

    - kubectl: 	kubectl version --client --short
    - kubeadm:	kubeadm version
    - kubelet:	kubelet --version
    - Control Plane: 	kubectl version --short




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
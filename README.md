# Jean-Edwards-Task

# VMs has been created

Obikiel1 and obikiel2

==============

# on Vm1 
- sudo apt update && sudo apt upgrade -y
- sudo apt install -y docker.io

## I then enabled and started docker

- —sudo systemctl enable docker
- —sudo systemctl start docker

## I then verified the installation of docker 
- —docker --version


## I Ran Rancher as a Docker container:

- docker run -d --restart=unless-stopped --privileged \
  -p 80:80 -p 443:443 \
  --name rancher rancher/rancher:latest


- Obikiel1 is the server for Rancher

====================================================

## Then I logged into the Rancher UI

![alt text](<Rancher-ui.png>)

## I then updated the password to “ $ugochukwu123”

![alt text](<Rancher-ui2.png>)

## I then created a new cluster

![alt text](<rancher-cluster.png>)
￼
## Registration command

- This command installs a Rancher system agent on a Linux machine to register it as a node in a Rancher-managed Kubernetes cluster.

- curl -fL https://20.84.119.220/system-agent-install.sh | sudo sh -s - --server https://20.84.119.220 --label 'cattle.io/os=linux' --token qtmhqwpggzn6gf2l6r9wh99z2zpzm8rrpnpsnfv8hv8d8zmts5wl6p --ca-checksum 79b2fd069b563d0a51ad97d8b0c2a32ed84629e1227edfdcac47b92043e5a0d1 --etcd --controlplane --worker

- curl --insecure -fL https://20.84.119.220/system-agent-install.sh | sudo sh -s - --server https://20.84.119.220 --label 'cattle.io/os=linux' --token qtmhqwpggzn6gf2l6r9wh99z2zpzm8rrpnpsnfv8hv8d8zmts5wl6p --ca-checksum 79b2fd069b563d0a51ad97d8b0c2a32ed84629e1227edfdcac47b92043e5a0d1 --etcd --controlplane --worker
￼

- I was able to get the cluster ACTIVE
￼
![alt text](<cluster-active.png>)

===============================================================

- On my local VM , I was able to access the nodes 


## Using terraform to install argo-cd
￼
- check main.tf


## I was able to confirm that argo cd has been deployed

![alt text](<argo-cd.png>)
￼
## I forwarded the  argo -cd server

- kubectl port-forward svc/argocd-server -n argocd 8080:443

￼
- I then proceed to retrieve the password and sign into  argo Cd

![alt text](<argo-sigin.png>)


## Then I applied the manifest in Argo-Cd

- “kubectl apply -f applications/app2.yaml -n argocd “

￼![alt text](<argo-manifest.png>)

=================================================================

## For some reason, my prometheus app was not monitoring or syncing
￼
![alt text](<Prometheus-app.png>)

## I was able to sync prometheus app
￼
![alt text](<Pro-sync.png>)
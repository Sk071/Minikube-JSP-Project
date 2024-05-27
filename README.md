Install Minikube using Docker

sudo apt install docker.io

sudo apt install -y apt-transport-https ca-certificates curl software-properties-common


curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
sudo dpkg -i minikube_latest_amd64.deb


sudo apt install minikube

****************************************************************************************************************

Install Kubectl 

 curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

 sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

 minikube start

 ****************************************************************************************************************

 install argocd inside minikube

 kubectl create namespace argocd

 kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml




 



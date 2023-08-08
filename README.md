# ArgoCD_Helm
In this repo I have a custom chart for mongodb and mongo-express that I deploy through ArgoCD .
# Installing Minikube

sudo su

# Now install docker

sudo apt update && apt -y install docker.io

# install Kubectl


curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
kubectl version --short

install Minikube

curl -Lo minikube https://github.com/kubernetes/minikube/releases/download/v1.24.0/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/

*****************************************************************************
# Install Conntrack
 apt install conntrack
*******************************************************************************
# Start Minikube
 minikube start --vm-driver=none
 minikube status

 ***************************************************************************

 # To download helm
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh

# To verify the installation use the following command
 
 which helm

# ArgoCD Installation

kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/core-install.yaml

# Port Forwarding

kubectl port-forward svc/argocd-server -n argocd 8080:443

# To get password

kubectl get secrets argocd-initial-admin-secret -n argocd -o yaml

# decode the password 

echo <password> | base64 --decode

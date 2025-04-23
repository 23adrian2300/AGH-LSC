# Lab 6 - Kubernetes
The main goal of this lab was to create a Kubernetes application. For this task I used minikube, and all was done in WSL2. 
## Used commands
**Downloading and installing minikube**
```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
sudo apt install -y curl
```
**Downloading and installing kubectl**
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install kubectl /usr/local/bin/kubectl
```
**Starting minikube with Docker driver**
```
minikube start --driver=docker
```
**Downloading and installing Helm**
```
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
helm repo add stable https://charts.helm.sh/stable
helm repo update
```
**Install the NFS Server/Provisioner with Helm**
```
helm install nfs-provisioner stable/nfs-server-provisioner \
  --set persistence.enabled=true \
  --set storageClass.name=nfs-storage
```
**Applying PVC/nginx-development/nginx-service/job**
```
kubectl apply -f pvc.yaml
kubectl apply -f nginx-deployment.yaml
kubectl apply -f nginx-service.yaml
kubectl apply -f job.yaml
```
**Exposing the nginx service**
```
minikube service nginx-service
```

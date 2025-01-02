# demo-kubeflow

git clone https://github.com/devopsifyco/demo-kubeflow.git

Setup cluster
minikube start --cpus 8 --memory 32768

Enable minikube addone
$ minikube addons enable metallb

$ minikube ip
    192.168.49.2

$ minikube addons configure metallb
-- Enter Load Balancer Start IP: 10.68.1.5
-- Enter Load Balancer End IP: 10.68.1.5
    ▪ Using image quay.io/metallb/speaker:v0.9.6
    ▪ Using image quay.io/metallb/controller:v0.9.6
✅  metallb was successfully configured

minikube image pull image:version

kubectl create deployment nginx --image nginx --port 80
kubectl get deployments,pods -l app=nginx
kubectl expose deployment nginx --type LoadBalancer --port 80 --target-port 80
kubectl get services -l app=nginx
curl -vk#L 'http://10.68.1.5/' | grep -o "<title>.*</title>"

minikube addons enable istio
minikube addons enable kubeflow
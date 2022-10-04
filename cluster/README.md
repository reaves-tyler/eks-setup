`helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx`

`helm repo update`

`helm upgrade --install ingress-nginx ingress-nginx/ingress-nginx --namespace ingress-nginx --set controller.service.type=LoadBalancer --version 4.2.0 --create-namespace`

`kubectl get service ingress-nginx-controller --namespace=ingress-nginx`

Get Loadbalancer External IP

`kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.9.1/cert-manager.crds.yaml`

`helm repo add jetstack https://charts.jetstack.io`

`helm repo update`

`helm install cert-manager jetstack/cert-manager --namespace cert-manager --create-namespace --version v1.9.1`

`kubectl get pods --namespace cert-manager`

Add Route53 Record

`kubectl apply -f lets-encrypt.yaml`

`kubectl apply -f ingress.yaml`

`kubectl create secret docker-registry dockerhub --docker-username= --docker-password= --docker-email=`

# eks-setup

The purpose of this repository is to setup a Kubernetes cluster on AWS with certificate management and demand-based compute autoscaling

Technologies:

- AWS CLI, kubectl, eksctl, helm
- AWS Elastic Kubernetes Service (EKS)
- Cluster Autoscaler
- Let's Encrypt
- cert-manager
- ingress-nginx

This guide does not include Kubernetes Deployments or Services. An example Ingress is provided. Find more information on how to create Deployments and Services:

- https://kubernetes.io/docs/concepts/workloads/controllers/deployment/
- https://kubernetes.io/docs/concepts/services-networking/service/

## Software Requirements

### AWS CLI

https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

### kubectl

https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/#install-with-homebrew-on-macos

### eksctl

`brew tap weaveworks/tap`
`brew install weaveworks/tap/eksctl`

### helm

`brew install helm`

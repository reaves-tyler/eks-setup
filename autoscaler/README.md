https://docs.aws.amazon.com/eks/latest/userguide/autoscaling.html

```
aws iam create-policy \
 --policy-name AmazonEKSClusterAutoscalerPolicy \
 --policy-document file://cluster-autoscaler-policy.json
eksctl utils associate-iam-oidc-provider --region=us-east-2 --cluster=my-cluster --approve
```

```
eksctl create iamserviceaccount \
 --cluster=my-cluster \
 --namespace=kube-system \
 --name=cluster-autoscaler \
 --attach-policy-arn=arn:aws:iam::918760427934:policy/AmazonEKSClusterAutoscalerPolicy \
 --override-existing-serviceaccounts \
 --approve
```

`kubectl apply -f cluster-autoscaler-autodiscover.yaml`

```
atch deployment cluster-autoscaler \
 -n kube-system \
 -p '{"spec":{"template":{"metadata":{"annotations":{"cluster-autoscaler.kubernetes.io/safe-to-evict": "false"}}}}}'
```

`kubectl -n kube-system edit deployment.apps/cluster-autoscaler`

         - --balance-similar-node-groups
         - --skip-nodes-with-system-pods=false

```
kubectl set image deployment cluster-autoscaler \
 -n kube-system \
 cluster-autoscaler=k8s.gcr.io/autoscaling/cluster-autoscaler:v1.22.3
```

`kubectl -n kube-system logs -f deployment.apps/cluster-autoscaler`

All the roles are working on AWS EKS

Roles:
- autoscaler(cluster autoscaler) is able to scale up and down nodes
- credentials is for authenticating ( so you can execute commands in EKS)
- aws-ingress is for using AWS ingress controller
- istioctl is for installing istio , will be used in combination with aws ingress
- kiali is a visual dashboard for istio
- keda is for scalling pods depending on external metrics, for example AWS SQS
- kube2iam is allowing pods to use annotation to access iam roles on AWS
- logging is for gathering logs from pods and sending them ( in this case to ElasticSearch )
- metrics-server is used to gather metrics
- testapp - simmple test app exposed with istio
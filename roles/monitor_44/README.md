#To upgrade to version 44.x - https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack

Careful with replica labels( replicaExternalLabelName: ) or it will mess the data, make sure is the same in the new deployment !
Careful compare values changes between versions. For example relabels , serviceMonitorSelectorNilUsesHelmValues , podMonitorSelectorNilUsesHelmValues

Run the following commands:

kubectl apply --server-side -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/v0.62.0/example/prometheus-operator-crd/monitoring.coreos.com_alertmanagerconfigs.yaml
kubectl apply --server-side -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/v0.62.0/example/prometheus-operator-crd/monitoring.coreos.com_alertmanagers.yaml --force-conflicts
kubectl apply --server-side -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/v0.62.0/example/prometheus-operator-crd/monitoring.coreos.com_podmonitors.yaml --force-conflicts
kubectl apply --server-side -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/v0.62.0/example/prometheus-operator-crd/monitoring.coreos.com_probes.yaml --force-conflicts
kubectl apply --server-side -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/v0.62.0/example/prometheus-operator-crd/monitoring.coreos.com_prometheuses.yaml --force-conflicts
kubectl apply --server-side -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/v0.62.0/example/prometheus-operator-crd/monitoring.coreos.com_prometheusrules.yaml --force-conflicts
kubectl apply --server-side -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/v0.62.0/example/prometheus-operator-crd/monitoring.coreos.com_servicemonitors.yaml --force-conflicts
kubectl apply --server-side -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/v0.62.0/example/prometheus-operator-crd/monitoring.coreos.com_thanosrulers.yaml --force-conflicts

kubectl delete daemonset -n monitoring -l app=prometheus-node-exporter

Now you can execute the Ansible role
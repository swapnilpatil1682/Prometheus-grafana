# Prometheus-grafana
This repo is about implementing prometheus and grafana in Kubernetes cluster using helm.


VIMP : 
https://itnext.io/kubernetes-monitoring-with-prometheus-in-15-minutes-8e54d1de2e13

To make use of that functionality the --kubelet-service argument must be passed to the Prometheus Operator when running it.



helm install coreos/prometheus-operator --name prometheus-operator --namespace  test-prometheus -f  <Run with values.yaml> 
helm install coreos/kube-prometheus --name kube-prometheus --set global.rbacEnable=true --namespace test-prometheus 

kubectl port-forward -n test-prometheus prometheus-kube-prometheus-0 9090

kubectl port-forward $(kubectl get  pods --selector=app=kube-prometheus-grafana -n  test-prometheus  --output=jsonpath="{.items..metadata.name}") -n  test-prometheus  3000

kubectl port-forward -n test-prometheus alertmanager-kube-prometheus-0 9093

Use the values-prometheus.yaml to install prometheus operator using helm 



helm repo add coreos https://s3-eu-west-1.amazonaws.com/coreos-charts/stable/


helm install coreos/prometheus-operator --name prometheus-operator --namespace  test-prometheus  -f valus-prometheus.yaml 





Use the kube-prometheus-values.yaml to install kube-prometheus using helm. 



helm install coreos/kube-prometheus --name kube-prometheus --set global.rbacEnable=true -f kube-prometheus-values.yaml   --namespace monitoring



$ kubectl port-forward -n monitoring prometheus-kube-prometheus-0 9090


$ kubectl port-forward $(kubectl get  pods --selector=app=kube-prometheus-grafana -n  monitoring --output=jsonpath="{.items..metadata.name}") -n monitoring  3000


$ kubectl port-forward -n monitoring alertmanager-kube-prometheus-0 9093

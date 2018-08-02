Use the kube-prometheus-values.yaml to install kube-prometheus using helm. 




helm install coreos/kube-prometheus --name kube-prometheus --set global.rbacEnable=true -f kube-prometheus-values.yaml   --namespace monitoring

# Below command will try to install prometheus instance monitoring frontend server. The configuration file used is values-prometheus-frontendserver.yam.
# PLEASE make sure to use the correct label selector in servicemonitorselector section.
# As we have label for service of front-end with label app: frontend-server-master that is why we have used the same label in servicemonitor selector in
# configuration file.

helm install coreos/prometheus --name prometheus-frontend-server -n=monitoring -f values-prometheus-frontendserver.yaml

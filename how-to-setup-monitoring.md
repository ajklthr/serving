# Prometheus

Install Eventing

Follow - https://knative.dev/docs/serving/observability/metrics/collecting-metrics/#setting-up-prometheus
https://github.com/knative/eventing/blob/main/DEVELOPMENT.md

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install prometheus prometheus-community/kube-prometheus-stack -n default -f values.yaml
# values.yaml contains at minimum the configuration below



# Grafana 

helm repo add grafana https://grafana.github.io/helm-charts

helm install grafana grafana/grafana

Note: When configuring prometheus as data source use its cluster IP

Run- kubectl apply -f https://raw.githubusercontent.com/knative-sandbox/monitoring/main/grafana/dashboards.yaml


1. Get your 'admin' user password by running:

   kubectl get secret --namespace default grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo

2. The Grafana server can be accessed via port 80 on the following DNS name from within your cluster:

   grafana.default.svc.cluster.local

   Get the Grafana URL to visit by running these commands in the same shell:
   export POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/name=grafana,app.kubernetes.io/instance=grafana" -o jsonpath="{.items[0].metadata.name}")
   kubectl --namespace default port-forward $POD_NAME 3000

3. Login with the password from step 1 and the username: admin

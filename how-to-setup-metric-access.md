https://kubernetes.io/docs/tasks/access-application-cluster/access-cluster/

kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
kubectl get deployment metrics-server -n kube-system

kubectl create serviceaccount metrics-admin

kubectl create clusterrolebinding metric-admin-role-bind --clusterrole=cluster-admin --serviceaccount=default:metrics-admin

kubectl create -f metricadmin.yaml


Note issue on minikube - https://github.com/kubernetes-sigs/metrics-server/issues/917

APISERVER=$(kubectl config view --minify | grep server | cut -f 2- -d ":" | tr -d " ")
TOKEN=$(kubectl describe secret metricsadmin | grep -E '^token' | cut -f2 -d':' | tr -d " ")

curl $APISERVER/api --header "Authorization: Bearer $TOKEN" --insecure

curl $APISERVER/metrics --header "Authorization: Bearer $TOKEN" --insecure


Useful Links:

https://kubernetes.io/docs/tasks/access-application-cluster/access-cluster/




Useful function
kubectl get serviceaccounts
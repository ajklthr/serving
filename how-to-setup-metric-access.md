https://kubernetes.io/docs/tasks/access-application-cluster/access-cluster/


kubectl create serviceaccount metrics-admin

kubectl create clusterrolebinding metric-admin-role-bind --clusterrole=cluster-admin --serviceaccount=default:metrics-admin


$cat << EOF | kubectl create -f -

apiVersion: v1
kind: Secret
metadata:
name: metricsadmin
annotations:
kubernetes.io/service-account.name: default:metrics-admin
type: kubernetes.io/service-account-token


EOF

kubectl apply -f - <<EOF
apiVersion: v1
kind: Secret
metadata:
name: default-token
annotations:
kubernetes.io/service-account.name: default:metrics-admin
type: kubernetes.io/service-account-token
EOF

kubectl apply -f - <<EOF
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
name: test-admin
rules:
- apiGroups: [""]
  resources: ["pods", "nodes"]
  verbs: ["get", "watch", "list"]
EOF

kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml

Note issue on minikube - https://github.com/kubernetes-sigs/metrics-server/issues/917

APISERVER=$(kubectl config view --minify | grep server | cut -f 2- -d ":" | tr -d " ")
TOKEN=$(kubectl describe secret metricsadmin | grep -E '^token' | cut -f2 -d':' | tr -d " ")

curl $APISERVER/api --header "Authorization: Bearer $TOKEN" --insecure

curl $APISERVER/metrics --header "Authorization: Bearer $TOKEN" --insecure


Useful Links:

https://kubernetes.io/docs/tasks/access-application-cluster/access-cluster/




Useful function
kubectl get serviceaccounts
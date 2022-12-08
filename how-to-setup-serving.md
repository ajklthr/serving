minikube start --container-runtime=containerd

export KO_DOCKER_REPO='docker.io/arunjoykalathoor'

# Follow https://github.com/knative/serving/blob/main/DEVELOPMENT.md

kubectl apply -f ./third_party/cert-manager-latest/cert-manager.yaml
kubectl wait --for=condition=Established --all crd
kubectl wait --for=condition=Available -n cert-manager --all deployments

ko apply --selector knative.dev/crd-install=true -Rf config/core/
kubectl wait --for=condition=Established --all crd

ko apply -Rf config/core/

# Deploy Istio


kubectl apply -l knative.dev/crd-install=true -f https://github.com/knative/net-istio/releases/download/knative-v1.8.0/istio.yaml
kubectl apply -f https://github.com/knative/net-istio/releases/download/knative-v1.8.0/istio.yaml

kubectl apply -f https://github.com/knative/net-istio/releases/download/knative-v1.8.0/net-istio.yaml

kubectl --namespace istio-system get service istio-ingressgateway


kubectl apply -f https://github.com/knative/serving/releases/download/knative-v1.8.2/serving-default-domain.yaml

# Deploy sample Sevice

On minikube

kubectl patch configmap/config-domain \
-n knative-serving \
--type merge \
-p '{"data":{"127.0.0.1.nip.io":""}}'

minikube tunnel

kubectl apply -f ./sample/autoscale-go/service.yaml


curl -v -H "Host::autoscale-go.default.127.0.0.1.nip.io" "http://127.0.0.1:80?sleep=100&prime=10000&bloat=5"



Useful commands

kubectl describe configmap/config-domain --namespace knative-serving
kubectl patch configmap/config-domain --namespace knative-serving --type=json -p='[{"op": "remove", "path": "/data/127.0.0.1.sslip.io"}]'
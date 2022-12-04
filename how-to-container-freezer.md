# View freeze daemon set
kubectl get daemonset -n knative-serving

# View container freezer daemon pods

kubectl get pods -n knative-serving | grep 'freeze-daemon'

# Start Freeze Daemon
RUNTIME=containerd
RELEASE=v0.1.0
kubectl apply -f "https://github.com/knative-sandbox/container-freezer/releases/download/${RELEASE}/freezer-${RUNTIME}.yaml"

# Stop Freezer Daemon

kubectl delete  daemonset freeze-daemon-containerd -n knative-serving



# Evidence 1

What? Warm memory container takes less CPU - Impact of Warm Memory Container

1. Set autoscaling.knative.dev/min-scale: "3

2.  Opt out of aggressive probing 
 spec:
   containers:
    - image: gcr.io/knative-samples/autoscale-go:0.1
      readinessProbe:
      periodSeconds: 0 # opt out of aggressive probing

3. If already patched container freezer, remove using

   kubectl patch configmap/config-deployment -n knative-serving --type=json -p='[{"op": "remove", "path": "/data/concurrencyStateEndpoint"}]'

4. Take CPU Utilization of application before deploying freezer
   a.( @see SleepTalker https://github.com/knative-sandbox/container-freezer/tree/main/test/test_images) in idle state
5. Start the Freezer
    a) Start Freeze Daemon 
    b) Patch Concurrency Endpoint
       kubectl patch configmap/config-deployment -n knative-serving --type merge -p '{"data":{"concurrencyStateEndpoint":"http://$HOST_IP:9696"}}'
   
6. Retake the CPU Utilization
7. What is the difference in CPU utilization? Is there a difference in Memory?

# Evidence 2

Proactive scheduling + Warm memory container works  well.
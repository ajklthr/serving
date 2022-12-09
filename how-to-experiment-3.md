Test - Eviction

Config:
autoscaling.knative.dev/metric: rps
autoscaling.knative.dev/target: "4.2"
autoscaling.knative.dev/target-utilization-percentage: "70"
autoscaling.knative.dev/target-burst-capacity: "0"


          <PreciseThroughputTimer guiclass="TestBeanGUI" testclass="PreciseThroughputTimer" testname="Precise Throughput Timer" enabled="true">
            <doubleProp>
              <name>allowedThroughputSurplus</name>
              <value>1.0</value>
              <savedValue>0.0</savedValue>
            </doubleProp>
            <intProp name="batchSize">1</intProp>
            <intProp name="batchThreadDelay">0</intProp>
            <longProp name="duration">120</longProp>
            <intProp name="exactLimit">10000</intProp>
            <longProp name="randomSeed">0</longProp>
            <doubleProp>
              <name>throughput</name>
              <value>150</value>
              <savedValue>0.0</savedValue>
            </doubleProp>
            <intProp name="throughputPeriod">60</intProp>
          </PreciseThroughputTimer>


# Steps

kubectl apply -f sample/autoscale-go/exp-app-1.yaml
kubectl apply -f sample/autoscale-go/exp-app-2.yaml 